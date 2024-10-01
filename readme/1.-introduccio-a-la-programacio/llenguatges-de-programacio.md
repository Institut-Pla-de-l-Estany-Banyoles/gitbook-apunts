# Llenguatges de programació

Els **llenguatges de programació** són eines que permeten als programadors donar instruccions a un ordinador per executar tasques específiques. Un llenguatge de programació és un conjunt de regles i sintaxi que tradueix els algorismes creats per humans a un format comprensible per la màquina.

Podem classificar els llenguatges segons el seu nivell d'abstracció o segons el procediment que segueixen per ser executats (compilats o interpretats).

### **Nivell d'abstracció**

* **Llenguatges de baix nivell**: Com el **llenguatge assemblador**, són propers al codi màquina i interactuen directament amb el maquinari. Són difícils d'entendre per humans, però molt eficients per a l'ordinador.

<figure><img src="../../.gitbook/assets/image (2).png" alt="" width="320"><figcaption><p>Llenguatge de baix nivell</p></figcaption></figure>

* **Llenguatges d'alt nivell**: Com **Python, Java, C++**, són més comprensibles per a humans perquè utilitzen sintaxi més propera al llenguatge natural. Aquests llenguatges es tradueixen a codi màquina mitjançant compiladors o intèrprets perquè l'ordinador els pugui executar.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="203"><figcaption><p>Llenguatge d'alt nivell</p></figcaption></figure>

### **Llenguatges compilats o interpretats**

* **Compilats**: el codi font es tradueix completament a codi màquina mitjançant un programa anomenat **compilador** abans de ser executat. Un cop compilat, el programa es pot executar directament sense necessitat del codi font original.

C, C++, Pascal, Fortran, Haskell, Go, Rust...

* **Interpretats**: el codi font s'executa línia per línia mitjançant un **intèrpret**, que tradueix i executa el codi al mateix temps, sense una compilació prèvia. Això permet una execució més dinàmica, però també més lenta en comparació amb els llenguatges compilats.

Python, JavaScript, PHP, Ruby, Perl, Lua...

* **Híbrids:** el codi font primer es compila a un format intermedi (com el _bytecode_) i després s'interpreta en temps d'execució.&#x20;

Java, C#, Basic, Kotlin...

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="375"><figcaption><p>Procediment llenguatges híbrids</p></figcaption></figure>

{% hint style="info" %}
Podem fer un símil d'aquests diferents tipus de llenguatge i la feina que fa un traductor o intèrpret.&#x20;

* El llenguatge compilat, seria com que al traductor li donem un text o un llibre, ell se'l llegeix, el va traduïnt i al cap d'uns dies ens dona el text traduït.&#x20;
* En el cas del llenguatge interpretat, seria com la feina que fa l'interpret en una conferència. A mesura que l'orador fa el seu discurs, l'interpret el va traduïnt en directe a un segon idioma.

Com us podeu imaginar, el resultat final de la traducció serà diferent. Però els dos mètodes tenen els seus pros i contres.
{% endhint %}

Anem a veure una taula on es comparen els principals aspectes en què difereixen els llenguatges compilats, interpretats o híbrids.&#x20;

<table><thead><tr><th width="135"></th><th>Compilats</th><th>Interpretats</th><th>Híbrids</th></tr></thead><tbody><tr><td><strong>Velocitat d'execució</strong></td><td>Molt ràpida, ja que el codi es compila a codi màquina directe.</td><td>Més lenta, ja que el codi es tradueix línia per línia durant l'execució.</td><td>Ràpida, però sovint més lenta que els compilats purs.</td></tr><tr><td><strong>Flexibilitat durant desenvolu-pament</strong></td><td>Limitada, ja que cal recompilar després de cada canvi.</td><td>Molt flexible, es pot modificar i executar immediatament sense recompilació.</td><td>Més flexible que els compilats, però depèn d'una màquina virtual.</td></tr><tr><td><strong>Temps de compilació</strong></td><td>Requereix temps addicional abans de l'execució, sobretot en projectes grans.</td><td>No necessita compilació prèvia; execució immediata.</td><td>El bytecode intermedi requereix compilació, però més ràpid que la compilació completa.</td></tr><tr><td><strong>Seguretat</strong></td><td>Molt segura, el codi final no és llegible per humans.</td><td>Menys segura, ja que el codi font es distribueix llegible.</td><td>Segura, el bytecode no és directament llegible per humans.</td></tr><tr><td><strong>Depuració</strong></td><td>Més complexa, cal recompilar per cada canvi.</td><td>Més fàcil, ja que es pot veure el resultat línia per línia.</td><td>Més fàcil que els compilats, però depèn de l'entorn d'execució.</td></tr><tr><td><strong>Errors</strong></td><td>Els errors de sintaxi es detecten en el procés de compilació.</td><td>Els errors es detecten en temps d'execució.</td><td>Els errors de sintaxi es detecten durant la compilació del bytecode, però poden aparèixer altres errors en l'execució.</td></tr><tr><td><strong>Portabilitat</strong></td><td>Depèn del sistema operatiu, ja que es compila per a un maquinari específic.</td><td>Molt portable, ja que es pot executar a qualsevol sistema amb un intèrpret adequat.</td><td>Molt portable, el bytecode pot executar-se en qualsevol sistema amb una màquina virtual.</td></tr><tr><td><strong>Aplicació típica</strong></td><td>Aplicacions on la velocitat i el rendiment són crítics (jocs, sistemes operatius).</td><td>Scripts, aplicacions web, i prototipatge ràpid.</td><td>Aplicacions multiplataforma, programari empresarial (Java, .NET).</td></tr></tbody></table>
