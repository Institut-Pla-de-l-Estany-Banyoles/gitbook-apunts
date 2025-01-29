# Classes i Objectes

#### Què és una Classe?

Una **classe** és una plantilla que defineix les **propietats (atributs)** i els **comportaments (mètodes)** d'un objecte. La classe simplement és una descripció de les **característiques** i **capacitats** que pot tenir una entitat.

<figure><img src="../../.gitbook/assets/image (17).png" alt="" width="188"><figcaption></figcaption></figure>

#### Què és un Objecte?

Un **objecte** és una instància d'una classe. Cada objecte creat a partir d'una mateixa classe comparteix el comportament definit, però pot tenir valors propis per als atributs.

<figure><img src="../../.gitbook/assets/image (18).png" alt="" width="188"><figcaption></figcaption></figure>

***

Un objecte és la representació de qualsevol element en un sistema informàtic.





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
