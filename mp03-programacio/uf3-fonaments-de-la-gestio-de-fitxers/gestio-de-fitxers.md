# Gestió de fitxers

En Java, les classes `File` i `Path` són les responsables de les operacions d'E/S de fitxers. Realitzen les mateixes funcions, però pertanyen a paquets diferents.

### Classe java.io.File

Des de les primeres versions, Java ha proporcionat el seu propi paquet _java.io_, que conté gairebé totes les classes que podem necessitar per efectuar operacions d'entrada i sortida. La classe File és **una representació abstracta de les rutes de fitxers i directoris**

```java
File file = new File("fitxers/tutorial.txt");
```

Les instàncies de la classe `File` són immutables, és a dir, una vegada creada, la ruta abstracta representada per aquest objecte mai canviarà.

### Classe java.nio.file.Path

La classe `Path` forma part de l'actualització NIO2, que es va afegir a Java a partir de la versió 7. Proporciona **una API completament nova per treballar amb E/S**. Com l'antiga classe `File`, la classe `Path` també crea **un objecte que es pot utilitzar per localitzar un fitxer en un sistema de fitxers i totes les operacions** que es poden fer amb la classe `File`

```java
Path path = Paths.get("fitxers/tutorial.txt");
```

En comptes d'utilitzar un constructor com fem amb l'API de `File`, creem una instància de `Path` utilitzant el mètode estàtic [java.nio.file.Paths.get()](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/file/Paths.html#get\(java.lang.String,java.lang.String...\))

### Perquè NIO2 API

El paquet _java.io_ es va introduir amb la primera versió del JDK de Java, permetent realitzar accions d'E/S. Des de llavors, molts desenvolupadors han reportat molts inconvenients, funcionalitats que falten i problemes amb algunes de les seves capacitats.

