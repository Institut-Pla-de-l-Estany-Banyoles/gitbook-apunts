# Herència

L’herència és una eina fonamental per crear aplicacions **escalables** i està estretament relacionada amb la taxonomia, la ciència de la classificació. Aquest concepte permet organitzar elements en una estructura jeràrquica basada en les seves similituds i diferències.

Aquest enfocament és àmpliament utilitzat en biologia, on els éssers vius es classifiquen en espècies, gèneres, famílies, etc. Per exemple, un gat domèstic (_Felis catus_) i un linx ibèric (_Lynx pardinus_) comparteixen característiques pròpies de la família dels felins, com la pupil·la vertical i les urpes retràctils, però es diferencien en mida, hàbitat i costums d’alimentació.

<figure><img src="../../../.gitbook/assets/image (23).png" alt="" width="563"><figcaption></figcaption></figure>

En programació, aquest mateix concepte s'aplica per definir característiques generals en una superclasse i refinar-les progressivament en subclasses més específiques. Això evita la redundància i facilita la reutilització del codi.

<figure><img src="../../../.gitbook/assets/image (24).png" alt="" width="563"><figcaption></figcaption></figure>

L'herència és un mecanisme essencial en la **programació orientada a objectes (POO)** que permet que **una classe (subclasse) reutilitzi i ampliï les propietats i comportaments d'una altra classe (superclasse)**. Fomenta la reutilització de codi i facilita la creació de jerarquies de classes organitzades.

#### 📝 Per a què serveix l'herència?

* **Reutilització de codi:** Les subclasses aprofiten mètodes i atributs de la superclasse.
* **Extensió de funcionalitats:** Les subclasses poden sobreescriure comportaments.
* **Polimorfisme:** Una mateixa operació es comporta diferent segons la classe.
* **Organització jeràrquica:** Facilita la comprensió mitjançant jerarquies.

### 📌 Conceptes Clau

* **Superclasse:** Classe base que aporta atributs i mètodes.
* **Subclasse:** Classe derivada que hereta i pot ampliar i/o modificar comportaments.

### 💻 Exemples d'ús a Java

> 🟡 **Exemple:** Una classe _Persona_ amb _nom_ i _edat_, i subclasses _Alumne_ i _Professor_ amb mètodes propis.

Tant l'_Alumne_ com el _Professor_, també tenen un _nom_ i una _edat_, però a part de les característiques i capacitats que tenen per ser _Persona_, també tenen característiques específiques d'ells. Per exemple, un alumne pot _estudiar()_ i un professor pot _avaluar()_.

{% hint style="success" %}
En **Java**, per difinir que u**na subclasse hereda d'una superclasse**, utilitzem la paraula clau `extends`
{% endhint %}

#### Exemple 1: Herència bàsica

```java
class Persona {
    String nom;
    public void saludar() {
        System.out.println("Hola, sóc una persona.");
    }
}

class Alumne extends Persona {
    public void estudiar() {
        System.out.println("Estic estudiant.");
    }
}

class Professor extends Persona {
    public void avaluar() {
        System.out.println("Avaluant el treball.");
    }
}
```

#### Exemple 2: Ús de `super`

```java
class Persona {
    String nom;
    Persona(String nom) {
        this.nom = nom;
    }
}

//Un Alumne, a part de tenir la característica nom de Persona, també té escola.
class Alumne extends Persona {
    String escola;
    
    Alumne(String nom, String escola) {
        super(nom);
        this.escola = escola;
    }
}
```

> ℹ️ **Nota:** `super` crida el constructor de la superclasse.

{% hint style="info" %}
`super`, fa referència a la superclasse. En aquest cas està cridant al constructor, però també podríem cridar mètodes o accedir a les propietats (en cas que tinguin la visibilitat com a `protected`) de les superclasses. `super.nom` o `super.saludar()`
{% endhint %}

### 🚧 Problemes Comuns

* ⚠️ **Pèrdua d'identitat:** Una subclasse tractada com a superclasse perd funcionalitats específiques.

```java
class Animal {
    void ferSoroll() {
        System.out.println("L'animal fa un soroll");
    }
}

class Gos extends Animal {
    void bordar() {
        System.out.println("El gos borda");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Gos();  // Upcasting
        a.ferSoroll();  // Correcte
        // a.bordar();  // Error: el compilador no reconeix el mètode bordar()
    }
}
```

* ⚠️ **Problema del diamant:** es produeix en llenguatges que permeten **herència múltiple** quan una subclasse hereta de dues superclasses que comparteixen una mateixa superclasse base. Això genera ambigüitats sobre quin mètode hauria d'executar-se. **Java no permet l'herència múltiple**, ho resol amb interfícies en comptes d'herència múltiple.
