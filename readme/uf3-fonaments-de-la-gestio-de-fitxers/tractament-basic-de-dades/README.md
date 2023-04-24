# Tractament bàsic de dades

Normalment, les aplicacions que fan servir fitxers no estan centrades en la gestió del sistema de fitxers ni tampoc de navegar per ell. L’objectiu principal d’usar fitxers és **poder emmagatzemar-hi dades o recuperar les que hi ha guardades**. Per tractar les dades d'un fitxer, és imprescindible **saber com s'organitzen** dins d'aquest. Podem emmagatzemar qualsevol mena de dades, el més important és saber que aquests valors s'hi guarden de manera seqüencial, un rere l'altre. Per tant, **la manera més habitual de tractar un fitxer és seqüencialment**.

## Lectura de fitxers

Per poder llegir fitxers orientats a caràcters, Java disposa de diferents classes com `Scanner` del paquet _java.utils_ o `Reader` del paquet _java.io._

### Classe [Scanner](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)

De la mateixa manera que llegim dades de l'entrada per defecte del programa, la consola, podem llegir d'un fitxer utilitzant la classe `Scanner`

```java
Path path = Paths.get("fitxers/tutorial.txt");

try (Scanner lector = new Scanner(path)) {
    while (lector.hasNextLine()) {
        String linia = lector.nextLine();
        System.out.println(linia);
    }
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
}
```

{% hint style="info" %}
Fixa't que aquet bloc try-catch és una mica diferent dels que haviem fet servir fins ara. Al costat del try hi ha un parametre. Aquest tipus de sentència s'anomena [_try-with-resources_](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html)
{% endhint %}

La sentència _try-with-resources_ és una instrucció que crea un o més recursos. **Un recurs és un objecte que s'ha de tancar quan el programa acaba d'utilitzar-lo**. El mateix bloc s'assegura que cada recurs es tanca al final de la sentència. Qualsevol objecte que implementi _java.lang.AutoCloseable_, incloent-hi tots els objectes que implementen _java.io.Closeable_, pot ser utilitzat com a recurs.

El següent codi seria equivalent a l'anterior:

```java
Path path = Paths.get("fitxers/tutorial.txt");

Scanner lector = null;
try {
    lector = new Scanner(path);
    while (lector.hasNextLine()) {
        String linia = lector.nextLine();
        System.out.println(linia);
    }
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
} finally {
    lector.close();
}
```

**Sempre cal tancar el fitxer un cop heu finalitzat totes les operacions d’entrada / sortida.**

### Classe [BufferedReader](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedReader.html)

Una altra manera simple de llegir fitxers és utilitzant la classe `BufferedReader`, que deriva de `Reader`. En el cas de fitxers grans és millor anar llegint i processant línia a línia.

```java
Path path = Paths.get("fitxers/tutorial.txt");

try (BufferedReader reader = Files.newBufferedReader(path)) {
    String line = null;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

{% hint style="info" %}
Cal tenir en compte que el mètode _readLine()_ retornarà _null_ quan s'arribi al final del fitxer.
{% endhint %}

### Fitxers petits

Per fitxers petits, podem **llegir-los tot de cop mitjançant** el mètode _static_ de la classe `Files` _Files.readAllLines()_. Aquest mètode ens torna una `List` de `String` on cada element és una línia del fitxer.

```java
Path path = Paths.get("fitxers/tutorial.txt");

List<String> read = null;
try {
    read = Files.readAllLines(path);
} catch (IOException e) {
    throw new RuntimeException(e);
}

System.out.println(read);
```

També es pot utilitzar el mètode _readAllBytes()_ en el cas de necessitar les dades en binari.

### Utilitzant Files.lines()

```java
Path path = Paths.get("fitxers/tutorial.txt");

try (Stream<String> lines = Files.lines(path)) {
    String data = lines.collect(Collectors.joining("\n"));
    System.out.println(data);
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

{% hint style="info" %}
Tant el mètdoe _readAllLines()_ com els _lines()_ poden rebre un segon paràmetre que configura la codificació del fitxer. Si no s'especifica, per omisió s'utilitza UTF-8.
{% endhint %}

### Llibreria externa [Apache Commons IO](https://commons.apache.org/proper/commons-io/)

Un altre possible manera de llegir fitxers en Java, és utilitzant la classe `FileUtils` de la llibreria externa _commons-io_

```java
File file = new File("fitxers/tutorial.txt");
String data = FileUtils.readFileToString(file, "UTF-8");
```

La mateixa llibreria també ofereix la classe `IOUtils`

```java
FileInputStream fis = new FileInputStream("fitxers/tutorial.txt");
String data = IOUtils.toString(fis, "UTF-8");
```



## Escriptura de fitxers

