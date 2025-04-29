# Escriptura

A continuació veurem diferents maneres d'escriure en un fitxer utilitzant Java. Farem ús de `BufferedWriter`, `PrintWriter` i utilitats de la classe `Files` de Java 7. Altres classes que existeixen, però que no veurem en detall són: `FileOutputStream`, `DataOutputStream`, `RandomAccessFile` i `FileChannel`.

## Classe [BufferedWriter](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedWriter.html)

Comencem amb una de les maneres més simples per **escriure un String en un fitxer**:

```java
File file = new File("fitxers/tutorial.txt");
String str = "Text a escriure";

try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))){
    writer.write(str);
} catch (IOException e) {
    e.printStackTrace();
}
```

{% hint style="danger" %}
Atenció! Tal com està creat el FileWriter, s'esborrarà el contingut previ del fitxer. Per poder **afegir una línia a un fitxer**, hem de crear el FileWriter amb el parametre append a true:&#x20;

```
public FileWriter(fileName, boolean append);
```
{% endhint %}

```java
File file = new File("fitxers/tutorial.txt");
String str = "Text a escriure";

try (BufferedWriter writer = new BufferedWriter(new FileWriter(file, true))){
    writer.append(str);
} catch (IOException e) {
    e.printStackTrace();
}
```

D'aquesta manera, el que estem fent és afegir una línia al final del fitxer.

## Classe [PrintWriter](https://docs.oracle.com/javase/7/docs/api/java/io/PrintWriter.html)

La classe `PrintWriter` ens permet **escriure text amb format** en un fitxer

```java
File file = new File("fitxers/tutorial.txt");
String str = "Text a escriure";

try (PrintWriter printWriter = new PrintWriter(new FileWriter(file))){
    printWriter.print(str);
    printWriter.printf("El nom de l'alumne és %s i la seva nota és %d, "Marc", 8);
} catch (IOException e) {
    e.printStackTrace();
}
```

Fixeu-vos com no només escrivim una cadena de text simple en un fitxer, sinó que també escrivim text formatat utilitzant el mètode _printf_. Podem crear l'escriptor utilitzant _FileWriter, BufferedWriter_ o fins i tot _System.out_.

## Classe [Files](https://docs.oracle.com/javase/7/docs/api/java/nio/file/Files.html)

La classe `Files` ens permet **escriure text amb format** en un fitxer

```java
Path path = Paths.get("fitxers/tutorial.txt");
String str = "Text a escriure";

byte[] strToBytes = str.getBytes();

try {
    Files.write(path, strToBytes);
} catch (IOException e) {
    e.printStackTrace();
}      
```

El mètode _write()_ rep com a paràmetre el `Path` on escriure, i un _byte\[]_ amb les dades a afegir-hi. També pot rebre un tercer paràmetre amb les opcions d'obertura del fitxer.

{% hint style="info" %}
Aquestes opcions d'obertura venen definit per l'enum [StandardOpenOption](https://docs.oracle.com/javase/7/docs/api/java/nio/file/StandardOpenOption.html) i els seus valors son: APPEND, CREATE, CREATE\_NEW, DELETE\_ON\_CLOSE, DSYNC, READ, SPARSE, SYNC, TRUNCATE\_EXISTING i WRITE
{% endhint %}
