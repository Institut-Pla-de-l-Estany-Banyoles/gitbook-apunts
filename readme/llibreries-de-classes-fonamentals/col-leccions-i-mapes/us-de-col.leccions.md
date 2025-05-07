# Ús de col.leccions

[Tota Collection és un Iterable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Collection.html), la qual cosa serveix per iterar qualsevol List, Set o Queue.

Per iterar tenim el mètode iterator():

```java
Iterator<Integer> iterator = list.iterator();
while(iterator.hasNext()) {
    Integer nextInt = iterator.next();
}
```

També es pot utilitzar el format for-each loop:

```java
for (Integer nextInt: list) {
    // ...
}
```

Hi ha dos mètodes d'Object que utilitzem en relació a les col·leccions, i que sovint cal sobreescriure:

* `public int hashCode()`: retorna un sencer diferent per a cada objecte. Si `equals()` retorna `true`, han de retornar el mateix sencer. S'utilitza per a inserir i cercar a col·leccions que utilitzen taules hash.
* `public boolean equals(Object obj)`: retorna `true` si els dos objectes es consideren iguals. Si es retorna `true`, cal que també hashCode() retorni el mateix sencer. `Object` té aquesta implementació per defecte: `this == obj`, que significa que són el mateix objecte. Però sovint volem retornar `true` encara que no es tracti del mateix objecte. Per exemple, `Integer` retorna `true` si els dos objectes contenen el mateix valor `int`.

Implementació típica de `equals()`:

```java
public boolean equals(Object o){
    if (o == null)
        return false;
    if (!(o instanceof Treballador))
        return false;
    Treballador altre = (Treballador) o;
    return this.treballadorId == altre.treballadorId;
}
```

Implementació típica de `hashcode()`:

```java
public int hashCode(){
    return (int) treballadorId;
}
```

Implementació alternativa de `hashcode()` utilitzant `Objects`:

```java
public int hashCode(){
    return Objects.hash(treballadorId); // llista de camps de l'objecte
}
```

Altres mètodes **Collection\<E>**:

* `boolean add(E e);`
* `void clear();`
* `boolean contains(Object o);`
* `boolean isEmpty();`
* `boolean remove(Object o);`
* `int size()`

El mètode `contains()` utilitza el mètode `equals()` per veure si existeix l'element. Per tant, depèn de la implementació de cada classe. En el cas de `Integer`, la documentació diu:

* The result is `true` if and only if the argument is not `null` and is an `Integer` object that contains the same `int` value as this object.

Per tant, són iguals dos objectes Integer que contenen el mateix valor sencer. `Object` implementa el mètode `equals()` com la igualtat (`this == o`). Compte, perquè si es pretén sobreescriure el mètode `equals()`, sempre s'ha de sobreescriure també el mètode `hashcode()`. Veure `Objects.hash()`.

**List\<E>** afegeix operacions per posicions:

* `void add(int index, E element)`
* `E get(int index)`
* `E set(int index, E element)`
* `E remove(int index)`

La implementació més clàsica és la de `ArrayList`. `LinkedList` podria ser interessant si s'insereixen elements al començament amb freqüència.

**Set\<E>** és una col·lecció que no conté repeticions. O sigui, no hi ha dos elements tals que `e1.equals(e2)`. No conté mètodes addicionals respecte `Collection`.

Tenim tres implementacions:

* `HashSet` utilitza el `hashCode()` de la clau per a optimitzar l'accés als elements.
* `TreeSet` utilitza una estructura en arbre navegable segons l'ordre dels elements, que han de ser comparables (implementen la interfície Comparable). Es basa en `TreeMap`.
* `LinkedHashSet` permet navegar els elements segons l'ordre d'inserció.

**Queue\<E>** és una col·lecció amb el concepte associat de "cap" i "cua": lloc per on es treuen i s'afegeixen els elements:

* `boolean add(E e)`: afegeix un element a la cua (amb excepció).
* `boolean offer(E e)`: afegeix un element a la cua.
* `E remove():` esborra l'últim element al cap (amb excepció).
* `E poll():` esborra l'últim element al cap.
* `E element():` examina l''últim element al cap (amb excepció).
* `E peek():` examina l'últim element al cap.

Com es veu, hi ha dos mètodes per cada operació (afegir, esborrar, examinar), una amb excepció i una altra sense.

Dues de les possibles implementacions:

* `LinkedList`: la implementació més habitual.
* `PriorityQueue`: permet que la cua estigui ordenada mitjançant un comparador, en lloc d'utilitzar l'ordre en que s'afegeixen els elements.

**Deque\<E>** és una `Collection` i també una `Queue<E>`. Permet afegir i treure elements als dos costats de la col.lecció, 'first' i 'last'. També permet implementar una pila (classe deprecada Stack) amb els mètodes:

* `void push(E e)`: afegeix un element a la pila (cap)
* `E pop()`: treu un element de la pila (cap)
* `E peek()`: examina l'element de la pila (cap)

`LinkedList` també implementa `Deque`.
