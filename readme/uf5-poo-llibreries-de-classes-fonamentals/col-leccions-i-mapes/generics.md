# Genèrics

Els genèrics permeten que els tipus (classes i interfícies) siguin paràmetres a l’hora de definir classes, interfícies i mètodes. Un cop que s'instancien, els paràmetres són substituïts pels tipus reals.

Beneficis:

* **Controls de tipus més forts a la compilació**.

Un compilador Java aplica una verificació de tipus forta al codi genèric i emet errors si el codi viola la seguretat del tipus. La correcció d’errors en temps de compilació és més fàcil que arreglar errors d’execució, que poden ser difícils de trobar.

* **Eliminació de casts**. El següent codi requereix tipus:

```java
List list = new ArrayList();
list.add("hello");
String s = (String) list.get(0);
```

Quan es reescriu amb genèrics, no el requereix:

```java
List<String> list = new ArrayList<String>();
list.add("hello");
String s = list.get(0);   // no cast
```

* Permet als programadors **implementar algoritmes genèrics**.

Mitjançant l’ús de genèrics, els programadors poden implementar algoritmes genèrics que treballin en col·leccions de diferents tipus, es poden personalitzar i són de tipus segur i més fàcil de llegir.

Des de Java 7 podem estalviar-nos la definició del paràmetre de tipus del constructor, ja que Java l'infereix:

```java
List<String> list = new ArrayList<>();
```

## Mètodes genèrics

* Totes les declaracions genèriques del mètode tenen una secció de paràmetre tipus delimitada per claudàtors d'angle (\<i>) que precedeix el tipus de retorn del mètode ( en el següent exemple).
* Cada secció de paràmetres de tipus conté un o més paràmetres de tipus separats per comes. Un paràmetre tipus, també conegut com a variable de tipus, és un identificador que especifica un nom de tipus genèric.
* Els paràmetres de tipus es poden utilitzar per declarar el tipus de devolució i actuar com a marcadors per als tipus d’arguments passats al mètode genèric, que es coneixen com a arguments de tipus reals.
* El cos d'un mètode genèric es declara com el de qualsevol altre mètode. Tingueu en compte que els paràmetres de tipus només poden representar tipus de referència, no tipus primitius (com int, double i char).

```java
public <E> void printArray(E[] inputArray) {
    // Display array elements
    for (E element : inputArray) {
        System.out.printf("%s ", element);
    }
    System.out.println();        
}
```

## Paràmetres de tipus delimitat

Hi pot haver moments en què voldreu restringir els tipus de tipus que es permeten passar a un tipus de paràmetre. Per exemple, un mètode que opera sobre números només pot voler acceptar instàncies de Number o de les seves subclasses.

Per declarar un paràmetre de tipus delimitat, enumereu el nom del paràmetre del tipus, seguit de la paraula clau `extends`, seguit tipus delimitant.

```java
public <T extends Comparable<T>> T maximum(T x, T y, T z) {
    T max = x;   // assume x is initially the largest
    if (y.compareTo(max) > 0) {
        max = y;   // y is the largest so far
    }
    if (z.compareTo(max) > 0) {
        max = z;   // z is the largest now                 
    }
    return max;   // returns the largest object   
}
```

Es poden tenir múltiples tipus delimitats:

```java
<T extends Type1 & Type2>
```

## Classes genèriques

Una declaració de classe genèrica sembla una declaració de classe no genèrica, tret que el nom de classe sigui seguit per una secció de paràmetre tipus.

Com en els mètodes genèrics, la secció de paràmetres de tipus d'una classe genèrica pot tenir un o més paràmetres de tipus separats per comes. Aquestes classes es coneixen com a classes parametrizades o tipus parametrizats perquè accepten un o més paràmetres.

```java
public class Box<T> {
    private T t;
    public void set(T t) {
        this.t = t;
    }
    public T get() {
        return t;
    }
}
```

## Implementacions genèriques

Les interfícies genèriques es poden implementar bàsicament de dues formes: de forma genèrica o no, utilitzant un tipus específic.

Suposem que tenim la següent interfície genèrica:

```java
interface Container<T> {		
    T getValue();
}
```

Una implementació genèrica manté el paràmetre genèric:

```java
public class ContainerImpl<T> implements Container<T> {
    private T t;
    public ContainerImpl(T t) {
        this.t = t;
    }
    @Override
    public T getValue() {
        return t;
    }		
}
```

Una implementació no genèrica utilitza un tipus específic a la interfície:

```java
public class LongContainerImpl implements Container<Long> {
    private Long l;
    public LongContainerImpl(Long l) {
        this.l = l;
    }
    @Override
    public Long getValue() {
        return l;
    }
}
```

Així es podrien utilitzar aquestes dues implementacions:

```java
Container<String> strContainer = new ContainerImpl<>("test");
System.out.println(strContainer.getValue().toUpperCase());
		
Container<Long> longContainer = new LongContainerImpl(12L);
System.out.println(longContainer.getValue() * 2);
```

## Comodins

El comodí (?) permet referir-se a un tipus desconegut. Habitualment s'utilitza com a tipus d'un paràmetre, camp o variable local. Tenim diferents tipus:

* comodins delimitats per dalt: `? extends Foo`. El paràmetre permet Foo o qualsevol subtipus de Foo. Utilitzat si és un paràmetre només d'entrada d'un mètode.

```java
public static void process(List<? extends Foo> list) {
    for (Foo elem: list) {
        // ...
    }
}
```

* comodins no delimitats: `?`. El paràmetre permet qualsevol tipus.
* comodins delimitats per baix: `? super Foo`. Permet Foo o qualsevol supertipus de Foo. Utilitzat si és un paràmetre només de sortida d'un mètode.
