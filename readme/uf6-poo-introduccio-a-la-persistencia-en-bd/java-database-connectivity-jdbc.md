# Java Database Connectivity (JDBC)

JDBC (Java DataBase Connectivity): API estàndard que permet llençar consultes a una BD relacional.

**JDBC** és el model de persistència bàsic a Java. En funció de la **mida** i el **tipus de projecte** és possible que necessitem ajuda per implementar aspectes recurrents al codi:

* Operacions CRUD: si necessitem fer CRUD per moltes taules, seria una feina molt feixuga.
* Generació de queries SQL: ens facilita tenir queries universals ben formades (dialectes).
* Gestió de transaccions: gestió per threads de transaccions i connexions a la BBDD.
* Control de concurrència (optimista, pessimista): mecanismes amb versions/timestamps o amb bloqueig de files.

Els paquets java.sql y javax.sql formen part de Java SE i contenen un bon nombre d’interfícies i algunes classes concretes, que conformen l’API de JDBC. Els components principals de JDBC són: els **controladors**, les **connexions**, les **sentències** i els **resultats**.

## Controladors (drivers)

Un controlador JDBC és una col·lecció de classes Java que us permet connectar-vos a una determinada base de dades. Per exemple, MySQL té el seu propi controlador JDBC. Un controlador JDBC implementa moltes de les interfícies JDBC. Quan el codi utilitza un controlador JDBC determinat, en realitat només utilitza les interfícies estàndard JDBC. El controlador JDBC concret que s’utilitza s’amaga darrere de les interfícies JDBC. D’aquesta manera podeu connectar un nou controlador JDBC sense que el vostre codi ho noti.

Els drivers estan disponibles quan la llibreria (jar) corresponent està al classpath. Per exemple, per a MySQL 8.x podem comprovar-ho amb:

```java
try {
    Class.forName("com.mysql.cj.jdbc.Driver");
} catch (ClassNotFoundException e) {
    System.out.println(name + "Falta llibreria");
}
```

## Connexions (connections)

Una vegada carregat i inicialitzat un controlador JDBC, heu de connectar-vos a la base de dades. Es fa obtenint una connexió a la base de dades mitjançant l’API JDBC i el controlador carregat. Tota comunicació amb la base de dades es fa a través d’una connexió. Una aplicació pot tenir més d’una connexió oberta a una base de dades alhora, però cal estalviar connexions, ja que són cares, i tancar-les sempre.

Per obtenir una connexió, necessitem una URL, que és dependent de la BBDD concreta. Per exemple:

```
jdbc:mysql://localhost:3306/test
jdbc:sqlite:path/test.db
```

Podem obtenir una connexió:

```java
Connection connection = DriverManager.getConnection(url, user, password);
// sentències ...
connection.close();
```

Una manera alternativa, i recomanable, d'obtenir una connexió és utilitzant el try-with-resources, ja que Connection és un AutoCloseable.

```java
try (Connection connection = DriverManager.getConnection(url, user, password)) {
    // sentències ...
} catch (SQLException e) {
    e.printStackTrace();
}
```

## Sentències (statements)

Una setència és el que utilitzeu per executar consultes i actualitzacions a la base de dades. Podeu utilitzar alguns tipus diferents d’enunciats. Cada declaració correspon a una sola consulta o actualització. Tenim bàsicament dos tipus de sentències en funció de si la sentència SQL té o no paràmetres (comodins amb ?).

### Statement

```java
try (Statement st = connection.createStatement()) {
    int count = st.executeUpdate(sql1); // INSERT, UPDATE o DELETE
    // o bé...
    try (ResultSet rs = st.executeQuery(sql2)) { // SELECT
        // processament...
    }
}
```

### PreparedStatement

```java
try (PreparedStatement ps = conn.prepareStatement(sql)) {
    ps.setType1(1, valor1); // 1 a N, on Type pot ser Int, String...
    ps.setType2(2, valor2);
    int count = ps.executeUpdate(); // INSERT, UPDATE o DELETE
    // o bé...
    try (ResultSet rs = ps.executeQuery()) { // SELECT
        // processament...
    } 
}
```

### Conjunts de resultats (ResultSets)

Quan es realitza una consulta a la base de dades, s'obté un conjunt de resultats. A continuació, podeu recórrer aquest ResultSet per llegir el resultat de la consulta.

```java
try (ResultSet rs = st.executeQuery(sql)) { 
    while (rs.next()) {
        Type1 valor1 = rs.getType1(1);
        Type2 valor2 = rs.getType2(2);
        // o bé...
        Type1 valor1 = rs.getType1("nom_columna1");
        Type2 valor2 = rs.getType2("nom_columna2");
    }
}
```

## Inserció i obtenció d'una clau generada

De vegades es vol obtenir la clau que s'acaba de generar a una columna automàticament. Això es pot definir a MySQL amb AUTO\_INCREMENT o bé a PostgreSQL amb SERIAL. Es pot aconseguir en dos pasos:

1. utilitzant el paràmetre `Statement.RETURN_GENERATED_KEYS` quan es crea el `PreparedStatement`.
2. Obtenint el `ResultSet` mitjançant PreparedStatement.getGeneratedKeys(). Habitualment només hi haurà una columna, la posició 1.

```java
int key;
String sql = "INSERT INTO taula (valor) VALUES (?)";       
try (PreparedStatement ps = conn.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {                
    ps.setString(1, valor);
    ps.executeUpdate();
    try (ResultSet rs = ps.getGeneratedKeys()) {
        if (rs.next()) {
            key = rs.getInt(1);
        }
    }
}
```

## java.sql.Date, java.sql.Time, and java.sql.Timestamp

Aquestes classes estenen la funcionalitat d'altres Java per representar l'equivalent en SQL. Per exemple, java.sql.Date expressa el dia, mes i any. I java.sql.Time representa hora, minuts i segons. Finalment, java.sql.Timestamp representa java.util.Date fins als nanosegons.

**Conversions entre java.sql.Date i java.util.Date**: java.sql.Date estén (extends) java.util.Date. Per tant: tots els java.sql.Date són també java.util.Date.

En general, als nostres programes **sempre es pot utilitzar java.util.Date**, la data genèrica a Java.

Però a JDBC s'utilitza **java.sql.Date** en dos casos:

* `void PreparedStatement.setDate(int index, Date sdate)`. Per crear un java.sql.Date a partir d'un java.util.Date:
  * sdate = new java.sql.Date(udate.getTime()). Per exemple:
    * `preparedStatement.setDate(3, new java.sql.Date(tasca.getDataInici().getTime()));`
  * sdate = java.sql.Date.valueOf(LocalDate.of(yyyy, mm, dd)).
* `Date ResultSet.getDate(...)` retorna un `java.sql.Date`. Però no cal fer res especial: es pot assignar a un java.util.Date.
  * udate = sdate. Per exemple:
    * `tasca.setDataInici(result.getDate("data_inici"));`

## Excepcions

Les sentències SQL sobre JDBC poden generar excepcions [SQLException](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/java/sql/SQLException.html).

Aquest tipus d'excepció té mètodes que poden ajudar a entendre el problema que s'ha produït:

* `getErrorCode()`: codi específic del proveïdor
* `getSQLState()`: codi SQLState stàndard

Les excepcions poden passar per diferents motius:

* Problemes de comunicació: connectivitat o servidor parat.
* Problemes d'autenticació: credencials incorrectes.
* Errors de sintaxi SQL, associats a la subclasse `SQLSyntaxErrorException`. Són errors de programació.
* Errors de violació de constraints, associats a la subclasse `SQLIntegrityConstraintViolationException`. Indiquen que alguna constraint del DDL no es respectaria, com per exemple una Foreign Key, una Unique/Primary Key, etc. Aquest tipus es gestiona habitualment a l'aplicació per a detectar condicions recuperables.

## Transaccions

Una transacció és un conjunt d’accions que s’han de dur a terme com una **única acció atòmica**. O totes es fan, o cap.

Quan es vol implementar una transacció, és important que totes les operacions de lectura i escriptura que es fan sobre la base de dades es facin compartint una única `Connection`. Per altra banda, no és correcte compartir una `Connection` entre diferents fils.

Inicieu una transacció per aquesta invocació:

```java
connection.setAutoCommit(false);
```

Ara podeu continuar fent consultes i actualitzacions de taules. Totes aquestes accions formen part de la transacció.

Si alguna acció intentada dins de la transacció falla, haureu de desfer la transacció. Això es fa així:

```java
connection.rollback();
```

Si totes les accions tenen èxit, hauríeu de confirmar la transacció. Un cop es fa, les accions són permanents a la base de dades i no hi ha marxa enrera. Es fa així:

```java
connection.commit();
```

Exemple amb try/catch:

```java
try (Connection conn = factory.getConnection()) {
    conn.setAutoCommit(false);
    try {
        // sentències...
        conn.commit();
    } catch (Exception e) {
        conn.rollback();
        throw e; // excepcio original
    }
} catch (SQLException e) {
    throw new RuntimeException("error SQL", e);
}
```

En el cas que la mateixa `Connection` es vulgui utilitzar després sense transacció, caldria fer:

```java
// no creem la connection
conn.setAutoCommit(false);
try {
    // sentències...
    conn.commit();
} catch (Exception e) {
    conn.rollback();
    throw e; // excepcio original
} finally {
    conn.setAutoCommit(true);
}
```

## Pool de connexions

El pool de connexions és un conegut patró d’accés a dades, que té com a objectiu principal reduir les despeses implicades en la realització de connexions de bases de dades i en operacions de bases de dades de lectura / escriptura.

En poques paraules, un pool de connexions és, al nivell més bàsic, una implementació de memòria cau de connexió de bases de dades, que es pot configurar per adaptar-se a requisits específics.

Es poden implementar adhoc, utilitzar llibreries de tercers o bé les de les implementacions del controlador JDBC. Sempre que sigui possible, és millor utilitzar un pool de connexions que fer-ho amb DriverManager.getConnection(...). Un pool ens crea un objecte [javax.sql.DataSource](https://docs.oracle.com/en/java/javase/11/docs/api/java.sql/javax/sql/DataSource.html), que permet obtenir connexions amb el seu mètode getConnection(). A més, el mètode close() de la connexió no la tanca, per poder reutilitzar-la un altre cop.

```java
DataSource ds = // construir-lo segons la base de dades
Connection conn = ds.getConnection(); // obté una nova connexió
...
conn.close(); // retorna la connexió al pool (no la tanca)
```
