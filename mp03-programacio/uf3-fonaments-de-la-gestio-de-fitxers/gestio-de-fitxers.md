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

#### Gestió d'errors

El problema més comú és el maneig deficient dels errors. Molts mètodes **no ens proporcionen detalls sobre el problema trobat** o fins i tot no llancen excepcions.

Suposem que tenim un programa senzill que esborra un fitxer:

```java
File file = new File("fitxers/tutorial.txt");
boolean result = file.delete();
```

Aquest codi es compila i s'executa amb èxit sense cap error. Tot i això, trobem la variable `result` amb un valor _fals_, però no coneixem la raó de per què ha fallat l'operació. Potser el fitxer no existeix o el programa no té permisos per esborrar-lo.

Podem reescriure la mateixa funcionalitat amb la nova API NIO2

```java
Path path = Paths.get("fitxers/tutorial.txt");
Files.delete(path);
```

Ara el compilador ens obliga a gestionar una _IOException_. A més, l'excepció llançada conté detalls sobre el seu error que ens indicaran, per exemple, si el fitxer no existeix.

#### Suport de metadades

La classe `File` del paquet _java.io_ té un suport pobre per les metadades, el que pot provocar problemes en diferents plataformes amb operacions d'I/O que requereixen aquesta informació dels fitxers.

Les metadades podrien incloure **permisos**, **propietari** i **atributs de seguretat**. A causa d'això, la classe `File` no admet en absolut els enllaços simbòlics, i el mètode _rename()_ no funciona de manera consistent en diferents plataformes.

#### Escalabilitat i rendiment

Els mètodes de la classe File no escalen bé. Això pot generar problemes en alguns directoris amb una quantitat gran de fitxers. Llistar el contingut d'un directori **pot provocar un bloqueig i problemes en la gestió de memòria**.&#x20;



A causa d'aquests problemes, Oracle va desenvolupar la millorada API NIO2. **Sempre que sigui possible, s'hauria de mirar d'utilitzar el nou paquet **_**java.nio**_ en lloc de les classes antigues.

