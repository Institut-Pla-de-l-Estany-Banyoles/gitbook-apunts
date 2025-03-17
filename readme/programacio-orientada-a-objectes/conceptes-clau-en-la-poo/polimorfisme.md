# Polimorfisme

### 💡**Introducció**

El **polimorfisme** és un dels principis fonamentals de la Programació Orientada a Objectes (POO), juntament amb l'herència, l'encapsulació i l'abstracció. El terme prové del grec (_πολύ_ _polí_ ‘molts’, i _μορφή_ _morfé_ ‘forma, figura’) i significa moltes formes, fent referència a la capacitat d'un mateix mètode o operador de comportar-se de manera diferent segons el context.

Gràcies al polimorfisme, podem escriure codi més flexible i reutilitzable, evitant la duplicació i facilitant la mantenibilitat.

***

Podem distingir dos tipus de polimorfisme:

### **Polimorfisme en temps de compilació - `Overloading`**

També conegut com a **polimorfisme estàtic o sobrecàrrega de mètodes**, ocorre quan una classe defineix múltiples mètodes amb el mateix nom però **diferents signatures (nombre o tipus de paràmetres)**.

**Exemple en Java:**

```java
class Calculadora {
    int sumar(int a, int b) {
        return a + b;
    }
    
    double sumar(double a, double b) {
        return a + b;
    }
    
    int sumar(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculadora calc = new Calculadora();
        System.out.println(calc.sumar(2, 3));         // 5
        System.out.println(calc.sumar(2.5, 3.5));     // 6.0
        System.out.println(calc.sumar(2, 3, 4));      // 9
    }
}
```

Aquest mecanisme permet sobrecarregar operacions per adaptar-se a diferents tipus o quantitats de dades.

***

### **Polimorfisme en temps d'execució - `Overriding`**

També conegut com **polimorfisme dinàmic o sobreescriptura de mètodes**, ocorre quan una subclasse redefineix un mètode heretat de la seva superclasse, mantenint la mateixa signatura.

Això permet tractar un objecte de la subclasse com si fos de la superclasse, però executant la versió del mètode de la subclasse.

**Exemple en Java:**

```java
class Animal {
    void ferSoroll() {
        System.out.println("L'animal fa un soroll");
    }
}

class Gos extends Animal {
    @Override
    void ferSoroll() {
        System.out.println("El gos borda");
    }
}

class Gat extends Animal {
    @Override
    void ferSoroll() {
        System.out.println("El gat miola");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a1 = new Gos();
        Animal a2 = new Gat();
        
        a1.ferSoroll(); // "El gos borda"
        a2.ferSoroll(); // "El gat miola"
    }
}
```

Aquí, la variable `a1` és del tipus `Animal`, però quan cridem `ferSoroll()`, s'executa el mètode de la subclasse corresponent.&#x20;

A part de veure l'aplicació de la sobreescriptura de mètodes, aquí estem fent un `upcasting`, estem fent passar un objecte de la classe Gat i una de la classe Gos com un Animal.

{% hint style="info" %}
Quan hem estat implementant el mètode `toString()` a les classes que hem estat fent fins ara, el que feiem era **sobreescriure el mètode** `toString()` que defineix la classe `Object`. Ho podeu identificar fàcilment perquè veurem l'anotació `@override` a sobre la signatura del mètode.

En Java, tota classe hereda de la classe Object, no cal posar la paraula extends, ho fa automàticament.
{% endhint %}

***

### **Avantatges del polimorfisme**

✅ **Reutilització de codi**: Permet escriure codi genèric que pot treballar amb múltiples tipus de dades.

✅ **Extensibilitat**: Es poden afegir noves subclasses sense modificar el codi existent.

✅ **Flexibilitat**: Els objectes es poden tractar de manera abstracta sense perdre funcionalitats específiques.

***

### **Polimorfisme i interfícies**

Java utilitza **interfícies** per implementar polimorfisme sense necessitat d'herència. Això permet a una classe implementar múltiples comportaments diferents.

**Exemple:**

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

En aquest cas, `Ocell` i `Avio` implementen la interfície `Volador`, cosa que permet que siguin tractats de manera homogènia.

***
