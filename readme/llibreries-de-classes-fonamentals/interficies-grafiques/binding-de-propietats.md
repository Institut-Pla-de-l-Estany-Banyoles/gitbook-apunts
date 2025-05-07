# Binding de propietats

Una **propietat** és un atribut accesible públicament i que afecta el seu estat i/o comportament. Les propietats són observables: poden notificar a observadors de canvis. Poden ser només lectura, només escriptura o lectura i escriptura.

El **binding** de les dades, en aquest context, es refereix a la relació entre variables d'un programa per tal de mantenir-se sincronitzades. A les GUI ens permet mantenir sincronitzats elements de la capa de model amb els elements GUI corresponents. Això s'aconsegueix gràcies a la implementació del patró observador.

Tipus de binding:

* Eager (ansiós) o lazy (mandrós): si el valor de variable es recalcula immediatament quan ho fa la dependència, o només quan es llegeix. Les propietats de JavaFX utilitzen avaluació mandrosa.
* Unidireccional o bidireccional: si només es fa en una direcció la sincronització, o en les dues.

Exemple de binding unidireccional:

```java
IntegerProperty p1 = new SimpleIntegerProperty(1);
IntegerProperty p2 = new SimpleIntegerProperty(2);
p1.bind(p2); // p1 pren el valor de p2
p2.set(3);
int valor1 = p1.get(); // retorna 3
```

Exemple de binding bidireccional:

```java
IntegerProperty p1 = new SimpleIntegerProperty(1);
IntegerProperty p2 = new SimpleIntegerProperty(2);
p1.bindBidirectional(p2);
p2.set(3);
int valor1 = p1.get(); // retorna 3
p1.set(4);
int valor2 = p2.get(); // retorna 4
```

Els binding es poden fer a JavaFX utilitzant les propietats associades als elements gràfics. Per exemple:

```java
TextField tf1 = new TextField();
TextField tf2 = new TextField();
tf1.textProperty().bind(tf2.textProperty());
```

Per associar una etiqueta a una propietat del model de diferents tipus podem utilitzar el mètode `asString()`:

```java
Label l = new Label();
IntegerProperty p = new SimpleIntegerProperty(3);
l.textProperty().bind(p.asString());
```
