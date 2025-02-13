# Conceptes clau en la POO

La **Programació Orientada a Objectes (POO)** és un paradigma de programació que es basa en l’ús d’**objectes** per estructurar el codi i organitzar les funcionalitats d’un programa. Q**uatre conceptes fonamentals** de la POO són:

1. [**Encapsulació**](encapsulacio.md)
2. **Relacions entre Classes (**&#x41;ssociació, Agregació i Composició)
3. **Herència**
4. **Polimorfisme**

***

### 🔹 2. Relacions entre Classes **(**&#x41;ssociació, Agregació i Composició)

Per poder crear programes més rics i complets que ens permetin representar situacions més complexes, és imprescindible poder definir relacions entre les classes que el componen. És per això, que existeixen diferents tipus de relacions entre classes que és important conèixer. Això permet construir objectes més complexos combinant altres objectes.

En **Programació Orientada a Objectes (POO)**, els objectes poden interactuar entre si establint relacions. Aquestes relacions es classifiquen en **associació, agregació i composició**, que indiquen el nivell de dependència entre els objectes.

***

#### 1. Associació

📌 **Definició:**\
L’**associació** és una relació **general** entre dues classes, on un objecte pot referenciar un altre. Aquesta relació pot ser de dos tipus:

* **Unidireccional**: Un objecte coneix l'altre, però no a l'inrevés.
* **Bidireccional**: Els dos objectes es coneixen mútuament.

📌 **Exemple:** Un **Professor** pot estar associat amb una **Escola**.

```java
class Professor {
    private String nom;

    public Professor(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }
}

class Escola {
    private String nom;
    private Professor professor; // Associació amb la classe Professor

    public Escola(String nom, Professor professor) {
        this.nom = nom;
        this.professor = professor;
    }

    public void mostraInfo() {
        System.out.println("L'escola " + nom + " té el professor " + professor.getNom());
    }
}

public class ExempleAssociacio {
    public static void main(String[] args) {
        Professor p = new Professor("Joan");
        Escola e = new Escola("Escola Central", p);
        e.mostraInfo(); // L'escola Escola Central té el professor Joan
    }
}
```

📌 **Característiques:**\
\
✅ No implica una relació de propietat.\
✅ Un objecte pot existir sense l’altre.\
✅ Pot ser **unidireccional** o **bidireccional**.

📌 **Diferència entre composició i agregació**

* **Composició (forta):** L’objecte **depèn** completament de la classe que el conté.
* **Agregació (fluixa):** L’objecte pot existir de manera independent fora de la seva classe contenidora.

📌 **Exemple de Composició en Java:**
