---
hidden: true
---

# Page 1



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
