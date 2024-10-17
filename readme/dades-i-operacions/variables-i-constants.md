# Variables i constants

Les dades són una de les parts principals de qualsevol aplicació informàtica, qualsevol element que s'hagi de processar, analitzar, calcular, consultar, comparar... Serà una dada que està guardada en el nostre sistema informàtic, sigui de manera temporal o persistent.

A la programació, les dades que formen part de la nostra aplicació s'anomenen variables. Aquestes ens permeten accedir a les dades emmagatzemades al nostre ordinador.

Si en un programa hem de guardar el nom d'un alumne, podríem tenir una variable anomenada `nomAlumne` que guardi el valor "_Marc"._ D'aquesta manera, sempre que vulguem accedir o modificar la informació associada al nom de l'alumne, podrem fer servir `nomAlumne` per trobar-la.

<figure><img src="../../.gitbook/assets/nomAlumne (1) (1).png" alt="" width="256"><figcaption><p>Representació d'una variable</p></figcaption></figure>

Podem classificar variables segons diverses característiques:

### Mutabilitat

Les **constants** no deixen de ser variables amb la particularitat que **el seu valor no pot canviar durant l'execució** del programa, mentre que les **variables** sí que poden variar el seu valor.

Per exemple, si un programa gestiona una escola amb un màxim de 25 alumnes per classe, podem definir `CAPACITAT = 25`. Aquest valor no canviarà al llarg de l'execució del programa. Ara, si el dia de demà ens diuen que han ampliat l'escola i ara hi caben un màxim de 50 alumnes, podem inicialitzar la constant amb aquest nou valor i durant tota l'execució passarà a valdre aquest valor. Les **constants en Java es declaren en majúscula i separades per guions baixos**: `PAGE_NOT_FOUND_ERROR = 404`

### Existència

Podem classificar les variables segons la seva existència, **estàtiques o dinàmiques.** Les variables estàtiques existeixen durant tota l'execució, mentre que les dinàmiques o locals, només es creen i es destrueixen segons la necessitat, oferint més flexibilitat per gestionar memòria eficientment.

Les **variables estàtiques** es mantenen en la memòria durant tota l'execució del programa. Un cop arrenca el programa, es carreguen a la memòria juntament amb la resta d'instruccions del codi a executar.&#x20;

Per contra, les **variables dinàmiques** es creen i destrueixen a mesura que es necessiten durant l'execució del programa. La seva memòria es gestiona dinàmicament, és a dir, es crea quan es declara (normalment dins d'un mètode o funció) i s'allibera quan ja no és necessària.&#x20;

{% hint style="warning" %}
Totes aquestes variables que estem parlant són les que enmagatzemen dades de [tipus primitius](#user-content-fn-1)[^1]. Aquestes es troben a la **pila de memòria o** [**stack**](#user-content-fn-2)[^2]. No confondre amb els objectes creats mitjançant `new`, aquests elements es guarden a la **memòria dinàmica o** [**heap**](#user-content-fn-3)[^3]**.**
{% endhint %}

### Complexitat

Podem tenir variables simples que només emmagatzemen un valor o les compostes, que poden contenir més d'un valor o una combinació de dades.

**Variables simples** són aquelles que emmagatzemen un únic valor a la vegada. Són de tipus primitiu, com enter, caràcter o booleà. Cada variable simple només pot contenir un valor en un moment donat.&#x20;

**Variables compostes** són aquelles que poden emmagatzemar múltiples valors o dades. Solen ser col·leccions o estructures de dades com arrays o objectes que contenen altres variables.

{% hint style="info" %}
Al principi del mòdul només treballarem amb dades simples, però de seguida afegirem estructures de dades i tuples.
{% endhint %}

***

## Variables i constants en Java&#x20;

### Variables

Per poder a començar a utilitzar dades en els nostres programes, hem de **declarar les variables**. La declaració és la reserva d'aquell nom associat al tipus de dada que serà. El tipus permet saber quant d'espai ha de reservar-se per emmagatzemar aquesta variable. La nomenclatura per fer-ho en Java és la següent:

&#x20;       <mark style="color:red;">tipusVariable</mark> nomVariable;        //Declaració d'una variable

I no només això, per poder recuperar el valor d'una variable, aquesta primer ha de tenir un **valor assignat**. Si intentem llegir el valor d'una variable que mai se n'hi ha assignat un, ens trobarem amb un l'error:

{% hint style="danger" %}
<mark style="color:red;">Variable 'nomVariable' might not have been initialized.</mark>
{% endhint %}

El primer cop que assignem un valor a una variable en diem **inicialització**. Ho podem fer juntament a la  línia que la declaració o a posteriori.

&#x20;       //Declaració i inicialització d'una variable en una sola línia\
&#x20;        <mark style="color:red;">tipusVariable</mark> nomVariable = <mark style="color:blue;">valorInicialització</mark>;       &#x20;



&#x20;        //Declaració i inicialització d'una variable en dues línies\
&#x20;        <mark style="color:red;">tipusVariable</mark> nomVariable2;\
&#x20;        nomVariable2 = <mark style="color:blue;">valorInicialització</mark>;       &#x20;

Anem a veure de forma gràcia com seria aquest concepte dins el codi del nostre programa i la memòria de l'ordinador.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption><p>Declaració i inicialització d'una variable</p></figcaption></figure>

La línia de codi <mark style="color:red;">`int`</mark>`age =`<mark style="color:blue;">`21`</mark>`;` acaba reservant un espai de memòria de 4 bytes (el que ocupa un `int`), associat al nom `age` i amb el valor `21` emmagatzemat en aquest espai de memòria.

### Notació

En Java, hi ha una sèrie de condicions i regles que s'han de seguir per crear **noms de variables vàlids**. A continuació s'expliquen aquestes condicions:

1. #### Caràcters Vàlids
   * Els noms de variables només poden contenir **lletres (A-Z, a-z)**, **dígits (0-9)**, el **símbol del subratllat (\_)**, i el **símbol del dòlar ($)**.
   * El nom **no pot començar amb un dígit** (0-9).
   * No poden contenir espais en blanc
2. #### Sensibilitat a Majúscules i Minúscules (case-sensitive)
   * Els noms de variables són **case-sensitive**, és a dir, **distingeixen entre majúscules i minúscules**. Això vol dir que `Variable` i `variable` serien considerades dues variables diferents.
3. #### Paraules Reservades
   * No es poden utilitzar les **paraules reservades de Java** (com `int`, `class`, `for`, `if`, etc.) com a noms de variables.
4. #### Longitud
   * No hi ha un límit tècnic clar per la longitud del nom d'una variable, però és recomanable utilitzar noms curts però descriptius per fer el codi més llegible.
5. #### Noms Significatius
   * És una bona pràctica que els noms de variables siguin **significatius** i **fàcils de llegir**. Això fa que el codi sigui més comprensible per altres desenvolupadors (i per tu mateix).
6. #### Patrons Habituals per als Noms
   * Es recomana seguir l'estil **camelCase** per als noms de variables. En aquest estil, la primera lletra és minúscula i cada paraula següent comença amb majúscula.

```java
int x = 5;            // Vàlid
int _variable = 10;   // Vàlid però no recomenat
int $total = 100;     // Vàlid però no recomenat
int 1var = 20;        // Invàlid, no pot començar amb un número
int num alumnes = 10; // Invàlid, no pot contenir espais

int Variable = 10;    // Vàlid
int variable = 20;    // Vàlid, és una variable diferent

int class = 10;       // Invàlid, ja que `class` és una paraula reservada

int count = 5;        // Vàlid i recomanat (curt i descriptiu)
int c = 5;            // Vàlid, però poc descriptiu

int nombreEstudiants = 30;  // Vàlid i descriptiu
int n = 30;                 // Vàlid, però no descriptiu
```

### Constants&#x20;

Com ja hem vist a l'explicació de l'inici, les **constants** no deixen de ser variables amb la particularitat que **el seu valor no pot canviar durant l'execució** del programa, mentre que les **variables** sí que poden variar el seu valor.

Per tal d'informar a Java que una variable és constant, tenim l'identificador `final`. Per tant, per declarar una constant ho hem de fer de la següent forma:

&#x20;       <mark style="color:purple;">final</mark> <mark style="color:red;">tipusVariable</mark> NOM\_VARIABLE = <mark style="color:blue;">valorInicialització</mark>;

{% hint style="info" %}
Els noms de les constants no segueixen la nomenclatura camelCase, sinó UPPER SNAKE\_CASE. Els seus noms són tots en majúscula i cada paraula va separada per un guió baix \_.
{% endhint %}

[^1]: Els [**tipus primitius de Java**](dades-i-operacions-en-java.md#tipus-primitius) són tipus de dades bàsics que no es basen en cap altre objecte o classe, i emmagatzemen valors directament a la memòria. Aquests tipus ofereixen una manera eficient de treballar amb dades senzilles com números, caràcters o valors booleans.

[^2]: El **stack** és una àrea de memòria utilitzada per emmagatzemar variables locals i per gestionar les crides a funcions o mètodes. És una estructura de tipus LIFO (_Last In, First Out_), on les dades es col·loquen a la part superior de la pila i es treuen en ordre invers.

[^3]: El **heap** és una àrea de memòria més gran i desestructurada que s'utilitza per emmagatzemar objectes creats dinàmicament, és a dir, aquells que s'inicialitzen amb el mot clau `new`. La memòria del _heap_ no s'allibera automàticament, sinó que en llenguatges com Java, el _Garbage Collector_ s'encarrega de recuperar-la quan ja no hi ha referències a l'objecte.
