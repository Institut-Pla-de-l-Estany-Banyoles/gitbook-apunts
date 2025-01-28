---
hidden: true
icon: globe
---

# Programació Orientada a Objectes

La **Programació Orientada a Objectes (P.O.O.)** és un paradigma de programació que posa el focus en els **objectes** i les seves **capacitats** en lloc de la lògica i les accions. Divideix els programes en objectes que interactuen entre si per processar dades.&#x20;

### Objectiu de la P.O.O.:

* Facilitar el **disseny** i el **manteniment** del codi.
* Millorar la **reutilització** del codi mitjançant la creació de components modulars i independents.
* Representar problemes complexos mitjançant una estructura clara, basada en models del món real.

***

### Característiques Principals de la P.O.O.

#### 1. **Abstracció**

L'abstracció consisteix a simplificar un problema destacant només els detalls més importants d'una entitat i amagant-ne els aspectes menys rellevants.

Posem per cas que volem fer un programa que simuli una cursa de camells. Els camells a la realitat tenen moltes característiques i capacitats (o comportaments possibles).

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="176"><figcaption><p>Cursa de camells</p></figcaption></figure>

* **Característiques:** Pes, edat, color, pelatge, nom, raça, velocitat caminant, velocitat corrent...
* **Capacitats:** Beure, menjar, reproduir-se, defecar, orinar, caminar, córrer, aixecar-se, seure...

{% hint style="warning" %}
Penseu que per implementar el nostre joc de la cursa de camells necessitem que els nostres camells tinguin totes aquestes característiques?&#x20;
{% endhint %}

Aquí és on hem d'aplicar l'abstracció. Quines són les característiques i accions que han de tenir els nostres camells?

* **Exemple:** Quan utilitzem un cotxe, només necessitem saber com accelerar o frenar, però no ens importa com funciona el motor internament.
* En P.O.O., això es tradueix en **classes** que encapsulen només els detalls necessaris.

**Avantatge:** Ajuda a reduir la complexitat del sistema en centrar-se en el que realment importa.

#### 2. **Encapsulació**

L'encapsulació és el procés de combinar dades (atributs) i comportaments (mètodes) dins d'una única unitat: la classe. A més, protegeix aquestes dades limitant-ne l'accés mitjançant **modificadors de visibilitat** (`private`, `protected`, `public`).

* **Exemple:** Una classe `Banc` pot tenir un atribut `saldo` que només és accessible mitjançant mètodes `getSaldo()` o `retirar()`.

**Avantatge:** Incrementa la seguretat del codi evitant accessos directes i no controlats a les dades.

***

#### 3. **Herència**

L'herència permet a una classe (anomenada **subclasse**) reutilitzar i ampliar les propietats i comportaments d'una altra classe (anomenada **classe pare**).

* **Exemple:** Una classe `Animal` pot tenir subclasses com `Gat` o `Gos`, que hereten propietats generals com `nom` i `edat`, però també defineixen comportaments específics com `miolar()` o `bordar()`.

**Avantatge:** Reutilitza el codi i redueix la duplicació, ja que les funcionalitats comunes es defineixen a la classe pare.

***

#### 4. **Polimorfisme**

El polimorfisme permet utilitzar el mateix mètode per a diferents tipus d'objectes, però amb comportaments diferents.

* **Exemple:** Una classe `Forma` pot tenir un mètode `calcularArea()`. Les subclasses com `Cercle` i `Rectangle` implementaran aquest mètode de manera diferent segons la forma.

**Avantatge:** Fomenta la flexibilitat i facilita l'escalabilitat del sistema.

***

### Avantatges de la Programació Orientada a Objectes

1. **Reutilització del Codi:**
   * Mitjançant herència i polimorfisme, es poden utilitzar components ja desenvolupats sense necessitat de començar des de zero.
2. **Mantenibilitat:**
   * Les classes encapsulades i ben estructurades faciliten la modificació i depuració del codi.
3. **Modularitat:**
   * Divideix el programa en mòduls lògics (objectes i classes), fet que en facilita la comprensió i col·laboració.
4. **Seguretat:**
   * L'encapsulació protegeix les dades sensibles limitant-ne l'accés.
5. **Escalabilitat:**
   * És fàcil afegir noves funcionalitats al programa ampliant classes o creant-ne de noves.
6. **Modelatge Realista:**
   * Permet representar entitats del món real d'una manera més intuïtiva i clara.

***

### Exemple d'Abstracció i Encapsulació

#### Classe Abstracta `CompteBancari` (Abstracció)

```java
public abstract class CompteBancari {
    protected double saldo;

    public CompteBancari(double saldoInicial) {
        this.saldo = saldoInicial;
    }

    public abstract void retirar(double quantitat); // Abstracció del comportament
}
```

#### Característiques principals:

* **Basada en classes:** Els programes es desenvolupen a partir de classes, que defineixen el comportament i les propietats dels objectes.
* **Interacció d'objectes:** Els objectes col·laboren entre si per aconseguir funcionalitats més complexes.

#### Llenguatges que utilitzen P.O.O.:

* **Purs de P.O.O.:** Python, Ruby, Smalltalk.
* **Dissenyats per P.O.O.:** Java, C++, C#.
* **Simulen P.O.O.:** JavaScript, PHP (>=v4), Perl (>=v5).

***

### Conceptes Clau de la P.O.O.

#### 1. **Abstracció**

L'abstracció permet centrar-se només en els detalls essencials d'un objecte, ignorant els aspectes innecessaris. Això facilita el disseny i l'anàlisi del sistema.

#### 2. **Encapsulació**

Es tracta d'agrupament de dades i mètodes relacionats dins d'una mateixa entitat (classe). L'encapsulació protegeix les dades mitjançant modificadors de visibilitat (`private`, `protected`, `public`).

#### 3. **Polimorfisme**

Permet que el mateix mètode tingui comportaments diferents segons el context o l'objecte que l'utilitza. Per exemple, el mateix mètode pot processar objectes de tipus diferent.

#### 4. **Herència**

L'herència permet a una classe reutilitzar propietats i comportaments d'una altra classe. Això facilita la creació de jerarquies i la reutilització del codi.

***

### Classes i Objectes

#### Què és una Classe?

Una **classe** és una plantilla que defineix les **propietats (atributs)** i els **comportaments (mètodes)** d'un objecte. La classe simplement és una descripció de les **característiques** i **capacitats** que pot tenir una entitat.

<figure><img src="../.gitbook/assets/image (17).png" alt="" width="375"><figcaption></figcaption></figure>

#### Què és un Objecte?

Un **objecte** és una instància d'una classe. Cada objecte creat a partir d'una mateixa classe comparteix el comportament definit, però pot tenir valors propis per als atributs.

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="375"><figcaption></figcaption></figure>

Podem fer el símil del concepte de Classe com el plànol d'una casa i les cases que en poden sortir d'aquests com els Objectes. Tot i això, no és del tot precís, ja que la casa que en deriva de seguir un plànol, acaba sent sempre la mateixa.&#x20;

En el fons, l'objectiu de la Classe és definir les característiques comunes que tenen les cases. El nombre d'obertures, metres quadrats construïts, nombre de lavabos, nombre d'habitacions, nombre de plantes, distribució...&#x20;

Les diferents cases que nosaltres podem crear, seran les instàncies d'aquesta classe,&#x20;

Exemple:

```java
// Definició de la classe
class Persona {
    String nom;
    int edat;

    void presentar() {
        System.out.println("Hola, em dic " + nom + " i tinc " + edat + " anys.");
    }
}

// Creació d'objectes
public class ExemplePOO {
    public static void main(String[] args) {
        Persona persona1 = new Persona();
        persona1.nom = "Anna";
        persona1.edat = 25;
        persona1.presentar(); // Hola, em dic Anna i tinc 25 anys.
    }
}
```
