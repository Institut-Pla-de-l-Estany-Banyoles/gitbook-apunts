# Relació entre Classes

Per poder crear **programes més rics i complets** que ens permetin representar **situacions més complexes**, és imprescindible poder **definir relacions entre les classes** que el componen. És per això, que existeixen diferents tipus de **relacions entre classes** que és important conèixer. Això permet **construir objectes més complexos combinant altres objectes**.

En **Programació Orientada a Objectes (POO)**, els objectes poden interactuar entre si establint relacions. Aquestes relacions es classifiquen en **associació, agregació i composició**, que indiquen el nivell de dependència entre els objectes.

***

### 1. Associació

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

📌 **Característiques de l'Associació**\
✅ No implica una relació de propietat.\
✅ Un objecte pot existir sense l’altre.\
✅ Pot ser **unidireccional** o **bidireccional**.

***

### 2. Agregació (Relació _"té un"_)

📌 **Definició:**\
L'**agregació** és un tipus d'associació **fluixa**, on una classe conté una altra com a atribut, però els dos objectes **poden existir independentment**.

📌 **Exemple:** Un **Departament** pot tenir molts **Empleats**, però un **Empleat** pot existir sense estar associat a cap departament.

```java
class Empleat {
    private String nom;

    public Empleat(String nom) {
        this.nom = nom;
    }

    public String getNom() {
        return nom;
    }
}

// ------------------------------------------------------------

class Departament {
    private String nom;
    private List<Empleat> empleats; // Llista d'empleats associats

    public Departament(String nom, List<Empleat> empleats) {
        this.nom = nom;
        this.empleats = empleats;
    }

    public void mostraEmpleats() {
        System.out.println("Departament: " + nom);
        for (Empleat e : empleats) {
            System.out.println("- " + e.getNom());
        }
    }
}

// ------------------------------------------------------------

public class ExempleAgregacio {
    public static void main(String[] args) {
        Empleat e1 = new Empleat("Anna");
        Empleat e2 = new Empleat("Marc");

        Departament d = new Departament("Informàtica", Arrays.asList(e1, e2));
        d.mostraEmpleats();
    }
}
```

📌 **Característiques de l'Agregació:**\
✅ Una classe **té un altre objecte** com a atribut, però **poden existir per separat**.\
✅ L'objecte agregat **no depèn** de l'objecte contenidor.\
✅ Exemple clar: Un **cotxe té rodes**, no obstant això, una roda pot existir sense el cotxe.

### 3. Composició (Relació _"forma part de"_)

📌 **Definició:**\
La **composició** és un tipus d'agregació **forta**, on una classe **no pot existir sense l’altra**. Quan l'objecte contenidor s'elimina, els seus components també es destrueixen.

📌 **Exemple:** Un **Cos** té un **Cor**, i un cor no pot existir sense un cos; si el cos desapareix, el cor també.

```java
// Classe que representa un òrgan del cos humà
class Cor {
    public void bategar() {
        System.out.println("El cor està bategant...");
    }
}

// Classe que representa un cos humà
class Cos {
    private Cor cor; // El cor forma part del cos

    public Cos() {
        this.cor = new Cor(); // El cor es crea juntament amb el cos
    }

    public void viure() {
        cor.bategar();
    }
}

public class ExempleComposicio {
    public static void main(String[] args) {
        Cos persona = new Cos();
        persona.viure(); // El cor està bategant...
    }
}

```

📌 **Característiques de la Composició:**\
✅ L'objecte **contingut depèn totalment del contenidor**.\
✅ Quan l'objecte principal s'elimina, l'objecte compost també desapareix.\
✅ **Si el cos s'elimina (`Cos` es destrueix), el cor també es perd.**\
✅ No podem traslladar el cor a un altre cos en aquest model. (podríem definir-ho diferent i poder fer trasplantaments).

***

:thinking: A vegades no és fàcil distingir entre agregació o composició. Depèn com enfoquem el problema pot donar com a resultat un tipus de relació o altra.

Posem per cas l'exemple **Usuari** i **Adreça** depèn de com enfoquem la relació:

* 📌 **Si un Usuari té una Adreça única i exclusiva**, i aquesta no té sentit sense l’Usuari → **Composició**.
* 📌 **Si una Adreça pot existir sense un Usuari i ser reutilitzada per altres Usuaris** → **Agregació**.

**Quina opció triem?** En aquest cas, fem **composició**, perquè una **adreça sol estar associada de manera exclusiva a un Usuari**, i si eliminem l’Usuari, també hauríem d’eliminar la seva Adreça.

***

### **Diferències entre Associació, Agregació i Composició**

| Tipus de relació | Definició                                                    | Exemple                                                                    | Dependència             |
| ---------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------- | ----------------------- |
| **Associació**   | Relació general entre dues classes, una coneix l'altra.      | Un professor pot estar associat a una escola.                              | ❌ No hi ha dependència. |
| **Agregació**    | Un objecte conté un altre, però poden existir per separat.   | Un departament té empleats, però un empleat pot existir sense departament. | ⚠️ Relació fluixa.      |
| **Composició**   | Un objecte forma part d'un altre i no pot existir sense ell. | Un Cos té un Cor, i el Cor no té sentit sense el Cos.                      | ✅ Dependència total.    |
