# Variables i constants

Les dades són una de les parts principals de qualsevol aplicació informàtica, qualsevol element que s'hagi de processar, analitzar, calcular, consultar, comparar... Serà una dada que està guardada en el nostre sistema informàtic, sigui de manera temporal o persistent.

A la programació, les dades que formen part de la nostra aplicació s'anomenen variables. Aquestes ens permeten accedir a les dades emmagatzemades al nostre ordinador (generalment a la RAM).&#x20;

Si en un programa hem de guardar el nom d'un alumne, podríem tenir una variable anomenada `nomAlumne` que guardi el valor "_Marc"._ D'aquesta manera, sempre que vulguem accedir o modificar la informació associada al nom de l'alumne, podrem fer servir `nomAlumne` per trobar-la.

<figure><img src="../../.gitbook/assets/nomAlumne (1) (1).png" alt="" width="256"><figcaption><p>Representació d'una variable</p></figcaption></figure>

Les **constants** no deixen de ser variables amb la particularitat, que el seu valor no pot canviar durant l'execució del programa, mentre que les **variables** sí que poden variar.&#x20;

Per exemple, si un programa gestiona una escola amb un màxim de 25 alumnes per classe, podem definir `CAPACITAT = 25`. Aquest valor no canviarà al llarg de l'execució del programa. Ara, si el dia de demà ens diuen que han ampliat l'escola i ara hi caben un màxim de 50 alumnes, podem inicialitzar la constant amb aquest nou valor i durant tota l'execució passarà a valdre aquest valor. Les **constants en Java es declaren en majúscula i separades per guions baixos**: `PAGE_NOT_FOUND_ERROR = 404`

Podem classificar les variables segons la seva existència, **estàtiques o dinàmiques.** Les variables estàtiques existeixen durant tota l'execució, mentre que les dinàmiques o locals, només es creen i es destrueixen segons la necessitat, oferint més flexibilitat per gestionar memòria eficientment.

Les **variables estàtiques** es mantenen en la memòria durant tota l'execució del programa. Un cop arrenca el programa, es carreguen a la memòria juntament amb la resta d'instruccions del codi a executar.&#x20;

Per contra, les **variables dinàmiques** es creen i destrueixen a mesura que es necessiten durant l'execució del programa. La seva memòria es gestiona dinàmicament, és a dir, es crea quan es declara (normalment dins d'un mètode o funció) i s'allibera quan ja no és necessària.&#x20;

{% hint style="warning" %}
Totes aquestes variables que estem parlant són les que enmagatzemen dades de [tipus primitius](#user-content-fn-1)[^1]. Aquestes es troben a la **memòria automàtica o** [**stack**](#user-content-fn-2)[^2]. No confondre amb els objectes creats mitjançant `new`, aquests elements es guarden a la **memòria dinàmica o** [**heap**](#user-content-fn-3)[^3]**.**
{% endhint %}

[^1]: Els **tipus primitius de Java** són tipus de dades bàsics que no es basen en cap altre objecte o classe, i emmagatzemen valors directament a la memòria. Aquests tipus ofereixen una manera eficient de treballar amb dades senzilles com números, caràcters o valors booleans.

[^2]: El **stack** és una àrea de memòria utilitzada per emmagatzemar variables locals i per gestionar les crides a funcions o mètodes. És una estructura de tipus LIFO (_Last In, First Out_), on les dades es col·loquen a la part superior de la pila i es treuen en ordre invers.

[^3]: El **heap** és una àrea de memòria més gran i desestructurada que s'utilitza per emmagatzemar objectes creats dinàmicament, és a dir, aquells que s'inicialitzen amb el mot clau `new`. La memòria del _heap_ no s'allibera automàticament, sinó que en llenguatges com Java, el _Garbage Collector_ s'encarrega de recuperar-la quan ja no hi ha referències a l'objecte.
