# Classes abstractes i interfícies

Les **classes abstractes** i les **interfícies** són eines que permeten definir **estructures comunes** per a múltiples classes i establir **contractes d’implementació**.

* **Classes abstractes**: Són plantilles per a altres classes, poden contenir mètodes concrets i abstractes (sense implementació).
* **Interfícies**: Defineixen un conjunt de mètodes que han de ser implementats per qualsevol classe que les implementi.

Aquestes estructures ajuden a aconseguir una major modularitat, reutilització de codi i potencien el polimorfisme.

***

### **Classes Abstractes**

Una **classe abstracta** és una classe que **no es pot instanciar** (no es poden crear objectes d'aquesta classe) i pot contenir mètodes sense implementació que han de ser definits per les subclasses.

#### **🔹 Característiques de les classes abstractes**

✔️ Pot contenir **atributs i mètodes concrets**.\
✔️ Pot tenir **mètodes abstractes** que les subclasses han de sobreescriure.\
✔️ No es pot instanciar directament.\
✔️ S'utilitza quan hi ha un comportament comú entre múltiples classes relacionades.

#### **🔹 Exemple en Java**

```java
abstract class Animal {
    String nom;
    
    Animal(String nom) {
        this.nom = nom;
    }
    
    abstract void ferSoroll(); // Mètode abstracte
    
    void dormir() {
        System.out.println(nom + " està dormint.");
    }
}

class Gos extends Animal {
    Gos(String nom) {
        super(nom);
    }
    
    @Override
    void ferSoroll() {
        System.out.println(nom + " borda!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal gos = new Gos("Rex");
        gos.ferSoroll();  // "Rex borda!"
        gos.dormir();      // "Rex està dormint."
    }
}
```

En aquest cas, `Animal` és una classe abstracta que defineix un mètode `ferSoroll()`, que ha de ser implementat per qualsevol subclasse, com `Gos`.

***

### **Interfícies**

Una **interfície** és una col·lecció de mètodes **sense implementació** que una classe ha d'implementar. A diferència de les classes abstractes, una classe pot implementar **múltiples interfícies**.

#### **🔹 Característiques de les interfícies**

✔️ No pot tenir atributs d’instància (només constants `final`).\
✔️ Tots els seus mètodes són **abstractes per defecte** (fins a Java 8, on es van introduir els `default methods`).\
✔️ Una classe pot implementar **múltiples interfícies**.\
✔️ Útil per definir **comportaments compartits** entre classes no relacionades per herència.

#### **🔹 Exemple en Java**

```java
interface Volador {
    void volar();
}

class Ocell implements Volador {
    public void volar() {
        System.out.println("L'ocell vola");
    }
}

class Avio implements Volador {
    public void volar() {
        System.out.println("L'avió vola");
    }
}

public class Main {
    public static void main(String[] args) {
        Volador v1 = new Ocell();
        Volador v2 = new Avio();
        
        v1.volar(); // "L'ocell vola"
        v2.volar(); // "L'avió vola"
    }
}
```

Aquí, `Ocell` i `Avio` implementen la interfície `Volador`, cosa que permet que siguin tractats de manera homogènia.

{% hint style="info" %}
Podem veure les **interfícies** com a **classes abstractes pures**, classes abstractes que **no poden tenir ni cap atribut ni cap mètode implementat.** Tot i que les interfícies si que permeten atributs constants i&#x20;
{% endhint %}

***

### **Diferències entre Classes Abstractes i Interfícies**

| Característica        | Classes Abstractes                                  | Interfícies                                                               |
| --------------------- | --------------------------------------------------- | ------------------------------------------------------------------------- |
| **Instanciació**      | No es poden instanciar                              | No es poden instanciar                                                    |
| **Mètodes**           | Pot tenir mètodes concrets i abstractes             | Tots els mètodes són abstractes (excepte `default` i `static` en Java 8+) |
| **Atributs**          | Pot tenir atributs d’instància                      | Només permet constants (`final static`)                                   |
| **Herència múltiple** | Una classe només pot heretar d'una classe abstracta | Una classe pot implementar múltiples interfícies                          |

***

### **Quan utilitzar cadascuna?**

✅ **Usa una classe abstracta** quan necessites definir **atributs i mètodes compartits** entre diferents subclasses.

✅ **Usa una interfície** quan diferents classes han de compartir **un mateix comportament**, però no tenen relació directa per herència.

🎯 **Regla general:**\
\- Si vols compartir codi entre subclasses, usa una classe abstracta.\
\- Si només vols definir un contracte sense compartir implementació, usa una interfície.
