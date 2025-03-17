# Arrays (Taules)

Els **arrays**, són estructures que emmagatzemen un conjunt d’elements del mateix tipus. En els arrays, cada element té un índex que permet accedir-hi de manera directa.

<figure><img src="../../.gitbook/assets/image (11).png" alt="" width="354"><figcaption><p><a href="https://www.geeksforgeeks.org/applications-advantages-and-disadvantages-of-array-data-structure/">GeeksforGeeks.org</a></p></figcaption></figure>

Per definir un array, primer hem d'indicar el tipus d'elements que contindrà, seguit de les dimensions que tindrà i per últim el nom que li donarem.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt="" width="310"><figcaption></figcaption></figure>

Segons el nombre de `[]`, definim les dimensions que tindrà l'array. Java no té un límit de dimensions, però la màquina JVM les limita a 255.

| <img src="../../.gitbook/assets/image (3) (1) (1).png" alt="" data-size="original"> | <img src="../../.gitbook/assets/image (5) (1).png" alt="" data-size="original"> |
| :---------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------: |

Un **array unidimensional** (també anomenat **vector**) és una llista lineal d’elements del mateix tipus. Cada element està identificat per un índex numèric, començant per 0.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Definició i creació d'un vector</p></figcaption></figure>

Els arrays multidimensionals permeten emmagatzemar dades en diverses dimensions. L'array més comú és el **bidimensional** (**matriu** o **taula**), que es pot visualitzar com una taula amb files i columnes. També es poden crear arrays de tres o més dimensions, però són menys comuns.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Definició i creació d'una matriu</p></figcaption></figure>

**Declaració**

{% tabs %}
{% tab title="Una dimensió" %}
```java
int[] numeros; //Declarem un array d'enters
int[] edats = new int[5] //Declarem un array d'enters amb espai per 5 elements.
```
{% endtab %}

{% tab title="Dues dimensions" %}
```java
int[][] temps;    //Declarem un array de dues dimensions
int[][] matriu = new int[3][3];  //Declarem i reservem espais matriu de 3x3
```
{% endtab %}

{% tab title="N dimensions" %}
```java
//Afegim tants [] com dimensions hagi de tenir la taula
int[][][][] ... [] dades;    //Declarem un array de N dimensions
```
{% endtab %}
{% endtabs %}

**Inicialització directa**

{% tabs %}
{% tab title="Una dimensió" %}
```java
int[] numeros = {1, 2, 3, 4, 5};    //Array d'enters amb valors inicials
String[] noms = {"tu", "jo", "ell"}
```
{% endtab %}

{% tab title="Dues dimensions" %}
```java
// Matriu d'enters amb els valors iniciats

int[][] dades = { {1, 2, 3}, {4, 5, 6}, {7, 8, 9} };

int[][] dades = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```
{% endtab %}
{% endtabs %}

#### Accés directe

Per accedir directament a un dels elements d'un array, hem de fer servir el seu índex. `nomArray[`<mark style="color:blue;">`index`</mark>`]`, tant podem fer-ho servir per consultar el seu valor com assignar-ne.&#x20;

{% tabs %}
{% tab title="Una dimensió" %}
```java
//Assignem el valor 40 al tercer element de l'array numeros
numeros[2] = 40
```
{% endtab %}

{% tab title="Dues dimensions" %}
```java
//Assignem el valor 10 al 4 element de la segona fila
dades[1][3] = 10
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
És important tenir en compte que l'índex del primer element d'un array és el 0
{% endhint %}

#### Accés seqüencial

Si en comptes d'accedir a un sol element puntual d'un array, volem accedir (tant si és per lectura com per escriptura) cada un dels elements d'un array, el que hem de fer és un recorregut. Per fer-ho, la forma més habitual és mitjançant un bucle `for` o un `for-each`

{% tabs %}
{% tab title="Una dimensió" %}
```java
//Donat un vector d'enters anomenat dades i amb 5 elements
int[] dades = new int[5];

//Mostrem cada un dels seus elements
for (int i = 0; i < dades.length; i++) {
    System.out.println(dades[i]);
}
```
{% endtab %}

{% tab title="Dues dimensions" %}
```java
//Donat un vector d'enters anomenat dades i amb 5 elements
int[][] taula = new int[2][5];

//Mostrem tots els elements. Per cada fila que tingui, recorrem tots els elements
for (int i = 0; i < taula.length; i++) {
    for (int j = 0; j < taula[i].length; j++) {
        System.out.println(taula[i][j]);
    }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Podem consultar la mida que té un array, mijançant la propietat `length` d'aquest. Podem recuperar el valor guardat dins aquesta propietat fent `nomArray.length`
{% endhint %}

Tal com hem comentat, també existeix l'iterador `for-each`. Aquest consulta  automàticament tots els elements d'un array sense haver de controlar l'índex. El codi següent dona el mateix resultat que l'anterior

```java
//Donat un vector d'enters anomenat dades i amb 5 elements
int[] dades = new int[5];

//Mostrem cada un dels seus elements
for (int dada : dades) {
    System.out.println(dada);
}
```

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

