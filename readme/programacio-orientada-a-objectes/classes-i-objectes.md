# Classes i Objectes

#### Què és una Classe?

Una **classe** és una plantilla que defineix les **propietats (atributs)** i els **comportaments (mètodes)** d'un objecte. La classe simplement és una descripció de les **característiques** i **capacitats** que pot tenir una entitat.

<figure><img src="../../.gitbook/assets/image (17).png" alt="" width="188"><figcaption></figcaption></figure>

#### Què és un Objecte?

Un **objecte** és una instància d'una classe. Cada objecte creat a partir d'una mateixa classe comparteix el comportament definit, però pot tenir valors propis per als atributs.

<figure><img src="../../.gitbook/assets/image (18).png" alt="" width="188"><figcaption></figcaption></figure>

***

Una **classe** és la representació abstracta d'un objecte. Hem de prendre les característiques indispensables per identificar els diferents tipus d'objectes que se'n poden crear d'aquesta i les accions.  És important analitzar quines **característiques (atributs)** i **capacitats (mètodes)** té el model que volem representar. L'**objecte** és la representació concreta que es crea a partir del motlle definit a la **classe**.

<figure><img src="../../.gitbook/assets/Class-Object.png" alt=""><figcaption></figcaption></figure>



Exemple:

```java
// Definició de la classe
class Persona {
    
    // Atributs
    String nom;
    int edat;
    
    // Mètodes
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
