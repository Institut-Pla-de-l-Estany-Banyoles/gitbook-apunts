# Herència

L’**herència** és el mecanisme que permet a una classe (subclasse) **heretar** atributs i mètodes d’una altra classe (superclasse). Això permet reutilitzar codi i definir relacions de jerarquia.

**Com es defineix en Java?**\
S’utilitza la paraula clau `extends` per indicar que una classe hereta d’una altra.&#x20;

**📌 Exemple d’Herència en Java**

```java
// Classe pare (superclasse)
class Animal {
    protected String nom;

    public void ferSoroll() {
        System.out.println("L'animal fa un soroll.");
    }
}

// Classe filla (subclasse) que hereta de Animal
class Gos extends Animal {
    public Gos(String nom) {
        this.nom = nom;
    }

    @Override
    public void ferSoroll() {
        System.out.println(nom + " borda.");
    }
}

public class ExempleHerencia {
    public static void main(String[] args) {
        Gos g = new Gos("Rex");
        g.ferSoroll(); // Sortida: Rex borda.
    }
}
```
