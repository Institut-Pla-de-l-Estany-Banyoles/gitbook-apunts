# Ús de mapes

Els mapes són estructures de dades dinàmiques que contenen correspondències entre parelles de clau i valor.

**Map\<K, V>** té aquestes operacions principals:

* `int size()`
* `boolean isEmpty()`
* `boolean containsKey(Object)`
* `V put(K, V)`
* `V remove(Object)`
* `void clear()`
* `Set<K> keySet()`
* `Collection<V> values()`
* `Set<Entry<K, V>> entrySet()`

El tipus Entry\<K, V> és una parella clau/valor immutable amb els mètodes:

* `K getKey()`
* `V getValue()`

<figure><img src="../../../.gitbook/assets/java-map-hierarchy.png" alt=""><figcaption><p><a href="https://www.javatpoint.com/java-map">Map Hierachy (javaTpoint)</a></p></figcaption></figure>

Les tres principals implementacions són:

* `HashMap` utilitza el `hashCode()` de la clau per a optimitzar l'accés als elements.
* `TreeMap` permet navegar els elements segons l'ordre natural d'aquests, que han de ser comparables (implementen la interfície Comparable).
* `LinkedHashMap`: permet navegar els elements segons l'ordre d'inserció.
