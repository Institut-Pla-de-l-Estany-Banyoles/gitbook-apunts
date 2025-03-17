# Encapsulació

Un dels **objectius de la programació orientada a objectes** és **l’encapsulació** de dades i de mètodes de manera que els programadors usuaris d’una classe només poden accedir a les dades mitjançant els mètodes que la mateixa classe proporciona.

El principi **d’encapsulació**, o d’**ocultació d’informació**, es basa en l’ocultació de les decisions de disseny, de manera que canvis en una classe afectin el mínim possible el programari ja desenvolupat.

L’**encapsulació** consisteix a restringir l’accés als atributs i mètodes d’un objecte per protegir les dades internes i evitar modificacions no controlades.

**Com s’aconsegueix?**

* Es declara els **atributs com a `private`** perquè no es puguin modificar directament.
* Es proporcionen **mètodes `getters` i `setters`** per controlar l’accés als atributs.

📌 **Exemple en Java:**

```java
public class Persona {
    private String nom;  // Atribut privat
    private int edat;

    // Constructor
    public Persona(String nom, int edat) {
        this.nom = nom;
        this.edat = edat;
    }

    // Getters i Setters
    public String getNom() {
        return nom;
    }

    public void setNom(String nom) {
        this.nom = nom;
    }

    public int getEdat() {
        return edat;
    }

    public void setEdat(int edat) {
        if (edat >= 0) { // Control per evitar valors negatius
            this.edat = edat;
        }
    }
}
```

📌 **Per què és útil?**

✅ Protegeix les dades d'accés no autoritzat.\
✅ Evita modificacions incorrectes dels atributs.\
✅ Permet validar dades abans de modificar-les.

