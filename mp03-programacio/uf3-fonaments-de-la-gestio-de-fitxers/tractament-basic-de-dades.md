# Tractament bàsic de dades

Normalment, les aplicacions que fan servir fitxers no estan centrades en la gestió del sistema de fitxers de l'ordinador ni tampoc de navegar per ell. L’objectiu principal d’usar fitxers és poder emmagatzemar-hi dades o recuperar les que hi ha guardades.
Per tractar les dades d'un fitxer, és imprescindible saber com s'organitzen dins d'aquest. Podem enmagatzemar qualsevol tipus de dades, el més important és saber que aquests valors s'hi guarden de manera seqüencial, un rere l'altre. Per tant, la manera més habitual de tractar un fitxer és seqüencialment.

## Lectura de fitxers

Per poder llegir fitxers orientats a caràcters, Java diposa de diferents classes com `Scanner` del paquet _java.utils_ o `Reader` del paquet _java.io_

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

### Classe [BufferedReader](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedReader.html)

### Utilitzant Java NIO

#### Fitxers petits

#### Fitxers grans

#### Utilitzant Files.lines()

