# Logging

El registre en logs (**logging**) permet organitzar d'una forma òptima els missatges generats en temps d'execució per un programari, i és una alternativa millor que els `System.out.println`. Té els següents avantatges:

* Permet assignar una prioritat als missatges, i posteriorment filtrar-los. Tant de forma global com per paquets (packages) i classes.
* Permet reencaminar els missatges a diferents destins, com consola, fitxer, etc.
* Permet adaptar el format dels missatges, com per exemple en text, en XML o a base de dades.

Java conté a la seva llibreria base el paquet `java.util.logging`. Aquest paquet pot ser utilitzat de forma bàsica de la següent forma:

```java
private static final Logger LOGGER = Logger.getLogger(LaMevaClasse.class.getName());
```

Aquesta sentència es pot afegir al començament d'una classe, per tal de fer-hi referència posteriorment. Per exemple:

```java
LOGGER.log(Level.INFO, "un missatge");
```

El primer paràmetre és el nivell de la notificació, i el segon el missatge. El nivell pot variar entre SEVERE (valor més alt), WARNING, INFO, CONFIG, FINE, FINER i FINEST (valor més baix).

A més, aquest mètode permet utilitzar paràmetres per posició amb el codi {0}, {1}... o passant una excepció.

```java
LOGGER.log(Level.FINE, "un missatge amb paràmetre {0}", "1");
LOGGER.log(Level.WARNING, "un missatge amb paràmetres {0} i {1}", new Object[]{"1", 2});
LOGGER.log(Level.SEVERE, "un missatge sense paràmetre i amb excepció", new RuntimeException("una excepció"));
```

Tot i que el mètode `log(String)` és el més estàndard i convenient, també hi ha mètodes de `Logger` per a cada nivell que faciliten l'escriptura:

```java
severe(String), warning(String), info(String), config(String), fine(String), finer(String), finest(String)
```

## Afegir persistència als Logs

Si no configurem un `FileHandler`, els logs simplement seran mostrats per la sortida estàndard. Si volem que aquests logs persisteixin per poder fer una anàlisi posterior o tenir un registre, hem de fer que aquests es vagin guardant en un fitxer a mesura que es llencin.

```java
FileHandler fh = null;
try {
    fh = new FileHandler("log.xml");
    LOGGER.addHandler(fh);
} catch (Exception e) {
    LOGGER.log(Level.SEVERE, "Error al crear el fitxer de logs", e);
}
LOGGER.log(Level.INFO, "Starting application...");
```

## Configuració

Si tenim un arxiu `loggingConfigFile` (tipus `File`) amb l'arxiu de configuració, hem de configurar el registre al començament de l'execució del programari mitjançant la classe [LogManager](https://docs.oracle.com/en/java/javase/11/docs/api/java.logging/java/util/logging/LogManager.html):

```java
LogManager.getLogManager().readConfiguration(new FileInputStream(loggingConfigFile));
```

Aquesta podria ser una configuració mínima amb nivell màxim de FINE que utilitza un formatador, [SimpleFormatter](https://docs.oracle.com/en/java/javase/11/docs/api/java.logging/java/util/logging/SimpleFormatter.html) per a la consola i un arxiu:

```
# two handlers defined:
handlers= java.util.logging.ConsoleHandler, java.util.logging.FileHandler

# default root level, overrided for package and for the LoggingTest class:
level = FINE
test.excepcions.level = INFO
test.excepcions.LoggingTest.level = FINEST

# console handler configuration (https://docs.oracle.com/en/java/javase/11/docs/api/java.logging/java/util/logging/ConsoleHandler.html)
java.util.logging.ConsoleHandler.level = FINEST
java.util.logging.ConsoleHandler.formatter = java.util.logging.SimpleFormatter

# default SimpleFormatter format
java.util.logging.SimpleFormatter.format=%1$tY-%1$tm-%1$td %1$tH:%1$tM:%1$tS.%1$tL %4$-7s [%3$s] %5$s %6$s%n

# file handler configuration (https://docs.oracle.com/en/java/javase/11/docs/api/java.logging/java/util/logging/FileHandler.html)
java.util.logging.FileHandler.level = ALL
java.util.logging.FileHandler.formatter=java.util.logging.SimpleFormatter
java.util.logging.FileHandler.pattern = %h/logging_test_%g.log
java.util.logging.FileHandler.limit = 1000000
java.util.logging.FileHandler.count = 10
```

El nivell FINE s'utilitza per defecte per tots els missatges. Es podria configurar per classe:

```
test.LoggingTest.level = FINEST
```
