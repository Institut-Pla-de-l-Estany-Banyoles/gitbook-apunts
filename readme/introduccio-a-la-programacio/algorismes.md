# Algorismes

Un algoritme és un conjunt d'instruccions ben definides i finites que s'han de seguir per resoldre un problema o realitzar una tasca. Aquestes instruccions se segueixen de manera seqüencial, i l'algorisme sempre ha de produir un resultat concret en un temps finit. Els algorismes es poden utilitzar en molts contextos, però són especialment comuns en programació i matemàtiques.

1. **Finitud**: Un algorisme ha de tenir un nombre finit de passos.
2. **No ambigüitat**: Cada pas de l'algorisme ha de ser clar i fàcil d'entendre.
3. **Entrada i sortida**: Té un o més inputs i genera un output.
4. **Efectivitat**: Cada pas ha de ser realitzable dins un temps raonable.

Podríem classificar els algoritmes en

* **Seqüencial**: S'executen les ordres en l'ordre escrit.
* **Iteratiu**: Repeteixen un conjunt d'instruccions mentre es compleix una condició.
* **Condicional**: L'execució varia en funció de certes condicions.

Però realment, els algoritmes que acabarem definint seran una combinació d'aquests tres tipus. Tindran parts seqüencials, iteratives i parts que només s'executaran si es compleixen certes condicions.

Podem representar els algoritmes en forma de text mitjançant **pseudocodi** o de forma gràfica mitjançant **diagrames de flux.**

### **Pseudocodi**&#x20;

És una forma simplificada d'expressar els passos d'un algorisme mitjançant un llenguatge natural o aproximat, sense seguir la sintaxi específica d'un llenguatge de programació fent servir paraules clau i estructures pròpies de programació. L'objectiu del pseudocodi és ser fàcil d'entendre per humans, sense preocupar-se dels detalls tècnics propis d'un llenguatge de programació concret.&#x20;

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt="" width="304"><figcaption></figcaption></figure>

A continuació podem veure diferents estructures de programació com les podem representar amb pseudocodi.

<table data-full-width="true"><thead><tr><th>Tipus d’estructura</th><th>Forma general</th><th>Descripció / Ús principal</th><th>Exemple aplicat</th></tr></thead><tbody><tr><td><strong>Seqüencial</strong></td><td><pre><code>INICI
  Instrucció 1
  Instrucció 2
FI
</code></pre></td><td>Executa instruccions una rere l’altra, en ordre.</td><td><pre><code>INICI
  Escriure "Introdueix el teu nom:"
  Llegir nom
  Escriure "Bon dia, ", nom
FI
</code></pre></td></tr><tr><td><strong>Condicional simple</strong></td><td><pre><code>SI condició LLAVORS
  Instruccions
FI SI
</code></pre></td><td>Executa un bloc només si la condició és certa.</td><td><pre><code>SI consum > 8 LLAVORS
  Escriure "Consum alt"
FI SI
</code></pre></td></tr><tr><td><strong>Condicional doble</strong></td><td><pre><code>SI condició LLAVORS
  Instruccions1
SINÓ
  Instruccions2
FI SI
</code></pre></td><td>Permet dues opcions: si la condició és certa o falsa.</td><td><pre><code>SI litres > 0 LLAVORS
  Escriure "Dades correctes"
SINÓ
  Escriure "Error"
FI SI
</code></pre></td></tr><tr><td><strong>Condicional múltiple</strong></td><td><pre><code>SEGONS variable FER
  CAS 1: Instruccions
  CAS 2: Instruccions
  CAS ALTRA: Instruccions
FI SEGONS
</code></pre></td><td>Selecciona un conjunt d’instruccions segons el valor d’una variable.</td><td><pre><code>SEGONS opció FER
  CAS 1: Escriure "Benzina"
  CAS 2: Escriure "Dièsel"
FI SEGONS
</code></pre></td></tr><tr><td><strong>Bucle MENTRE (WHILE)</strong></td><td><pre><code>MENTRE condició FER
  Instruccions
FI MENTRE
</code></pre></td><td>Repeteix mentre la condició sigui certa. La condició es comprova <em>abans</em> d’executar el bloc.</td><td><pre><code>MENTRE litres ≠ 0 FER
  Llegir km
  Calcula consum
  Llegir litres
FI MENTRE
</code></pre></td></tr><tr><td><strong>Bucle REPETIR...FINS (DO-WHILE)</strong></td><td><pre><code>REPETIR
  Instruccions
FINS condició
</code></pre></td><td>Garanteix almenys una execució abans de comprovar la condició.</td><td><pre><code>REPETIR
  Llegir litres
FINS litres = 0
</code></pre></td></tr><tr><td><strong>Bucle PER (FOR)</strong></td><td><pre><code>PER i := 1 FINS N FER
  Instruccions
FI PER
</code></pre></td><td>Repeteix un nombre fix de vegades.</td><td><pre><code>PER i := 1 FINS 5 FER
  Escriure "Hola!"
FI PER
</code></pre></td></tr><tr><td><strong>Declaració de variables</strong></td><td><pre><code>Definir nom com Tipus
</code></pre></td><td>Reserva espai i tipus per a cada dada.</td><td><pre><code>Definir litres, km com real
</code></pre></td></tr><tr><td><strong>Assignació de valors</strong></td><td><pre><code>variable := expressió
</code></pre></td><td>Dona un valor a una variable.</td><td><pre><code>consum := (litres / km) * 100
</code></pre></td></tr><tr><td><strong>Entrada / Sortida</strong></td><td><pre><code>Llegir variable
Escriure "Text", variable
</code></pre></td><td>Interacció amb l’usuari.</td><td><pre><code>Llegir nom
Escriure "Hola ", nom
</code></pre></td></tr></tbody></table>

### **Diagrames de flux**

Un **diagrama de flux** és una representació gràfica d'un procés o algorisme, utilitzant formes geomètriques com rectangles, diamants i fletxes per mostrar els passos i la seqüència que segueix el procés.

Aquest tipus de diagrama és molt útil per visualitzar processos complexos d'una manera fàcil d'entendre, facilitant l'anàlisi i la resolució de problemes. S'utilitza àmpliament en programació, negocis i altres àmbits per planificar o comunicar passos lògics o decisions.

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption><p>Diagrama de flux simple</p></figcaption></figure>

A continuació podeu veure les diferents formes i la utilitat que tenen, segueixen un estàndard definit per la norma **ISO 5807** (Documentació del procés d'informació). Aquest estàndard descriu els símbols més utilitzats en la representació d'algorismes i processos.

{% hint style="info" %}
Les principals formes són:

* **Oval:** inici o final de procés
* **Rectangle:** operacions o accions
* **Rombe:** decisions / bifurcacions
* **Fletxa:** flux de dades o execució
{% endhint %}

<figure><img src="https://cms.boardmix.com/images/articles/flowchart-symbols-cheatsheet.png" alt=""><figcaption><p>Blocs d'un diagrama de flux</p></figcaption></figure>

L'estandardització permet que els diagrames de flux siguin reconeguts i interpretats de manera consistent per qualsevol persona, facilitant la comunicació i anàlisi de processos en diferents àmbits, com programació, negocis o enginyeria.

{% hint style="info" %}
Algunes aplicacions online que podem utilitzar per dissenyar-ne poden ser:

* &#x20; [Draw.io](https://www.draw.io/)
* &#x20; [LucidChart](https://www.lucidchart.com/)
* &#x20; [Gliffy](https://www.gliffy.com/)
* &#x20; [VisualParadigm](https://online.visual-paradigm.com/diagrams/solutions/free-class-diagram-tool/)
* [  Diagrams.net](https://www.diagrams.net/)
* [  cacoo](https://cacoo.com/signup)
* &#x20; [Microsoft Visio](https://www.microsoft.com/es-es/microsoft-365/visio/flowchart-software)
{% endhint %}
