---
hidden: true
---

# Principis de Disseny SOLID

Els principis SOLID són un conjunt de cinc regles fonamentals per al disseny de programari orientat a objectes, introduïdes per **Robert C. Martin (Uncle Bob)**. Aquests principis ajuden a crear codi més net, modular i fàcil de mantenir.

Cada lletra de **SOLID** representa un principi:

1. **S** - Single Responsibility Principle (_Principi de Responsabilitat Única_)
2. **O** - Open/Closed Principle (_Principi Obert/Tancat_)
3. **L** - Liskov Substitution Principle (_Principi de Substitució de Liskov_)
4. **I** - Interface Segregation Principle (_Principi de Segregació d’Interfícies_)
5. **D** - Dependency Inversion Principle (_Principi d'Inversió de Dependències_)

***

## **Principis SOLID**

### **S - Single Responsibility Principle (SRP)**

Un mòdul o classe ha de tenir **una única responsabilitat** i només un motiu per canviar.

🔹 **Benefici:** Facilita la mantenibilitat i redueix el risc d’errors en modificar el codi.

**❌ Exemple incorrecte:**

```java
class Factura {
    void calcularTotal() { /* càlcul del total */ }
    void imprimirFactura() { /* generació del document */ }
    void guardarBD() { /* connexió i inserció a la base de dades */ }
}
```

📌 **Problema:** Aquesta classe fa **tres coses diferents**.

**✅ Exemple correcte (SRP aplicat):**

```java
class Factura {
    void calcularTotal() { /* càlcul del total */ }
}

class ImpressoraFactura {
    void imprimir(Factura factura) { /* impressió */ }
}

class RepositoriFactura {
    void guardar(Factura factura) { /* guardar a la BD */ }
}
```

📌 **Solució:** Cada classe **només** té una responsabilitat.

***

### **O - Open/Closed Principle (OCP)**

El codi ha d'estar **obert per a l'extensió però tancat per a la modificació**.

🔹 **Benefici:** Permet afegir funcionalitats sense modificar el codi existent, evitant regressions.

**❌ Exemple incorrecte:**

```java
class CalculadoraDescompte {
    double calcularDescompte(String tipus, double preu) {
        if (tipus.equals("NORMAL")) return preu * 0.05;
        else if (tipus.equals("VIP")) return preu * 0.10;
        else return 0;
    }
}
```

📌 **Problema:** Si es vol afegir un nou tipus de descompte, cal modificar la classe.

**✅ Exemple correcte (OCP aplicat):**

```java
interface Descompte {
    double aplicar(double preu);
}

class DescompteNormal implements Descompte {
    public double aplicar(double preu) { return preu * 0.05; }
}

class DescompteVIP implements Descompte {
    public double aplicar(double preu) { return preu * 0.10; }
}

class CalculadoraDescompte {
    double calcular(Descompte descompte, double preu) {
        return descompte.aplicar(preu);
    }
}
```

📌 **Solució:** Ara es poden afegir nous descomptes sense modificar `CalculadoraDescompte`.

***

### **L - Liskov Substitution Principle (LSP)**

Una subclasse ha de poder substituir la seva superclasse **sense trencar el codi existent**.

🔹 **Benefici:** Garanteix que les subclasses són realment una extensió de la superclasse i es comporten correctament.

**❌ Exemple incorrecte:**

```java
class Rectangle {
    int ample, alt;
    void setAmple(int a) { this.ample = a; }
    void setAlt(int a) { this.alt = a; }
}

class Quadrat extends Rectangle {
    void setAmple(int a) { this.ample = this.alt = a; }
    void setAlt(int a) { this.ample = this.alt = a; }
}
```

📌 **Problema:** `Quadrat` no es comporta com `Rectangle`, ja que `setAmple()` i `setAlt()` no tenen el mateix efecte.

**✅ Solució:** No hauríem de forçar la relació d’herència:

```java
interface Forma {
    int calcularArea();
}

class Rectangle implements Forma {
    int ample, alt;
    int calcularArea() { return ample * alt; }
}

class Quadrat implements Forma {
    int costat;
    int calcularArea() { return costat * costat; }
}
```

📌 **Solució:** Ara `Quadrat` i `Rectangle` compleixen correctament LSP.

***

### **I - Interface Segregation Principle (ISP)**

Les classes no haurien d’implementar interfícies que no utilitzen.

🔹 **Benefici:** Evita que una classe implementi mètodes innecessaris.

**❌ Exemple incorrecte:**

```java
interface Treballador {
    void treballar();
    void menjar();
}

class Robot implements Treballador {
    public void treballar() { /* treballa */ }
    public void menjar() { /* ??? */ }
}
```

📌 **Problema:** `Robot` no hauria de tenir el mètode `menjar()`.

**✅ Exemple correcte (ISP aplicat):**

```java
interface Treballador {
    void treballar();
}

interface Menjador {
    void menjar();
}

class Robot implements Treballador {
    public void treballar() { /* treballa */ }
}

class Persona implements Treballador, Menjador {
    public void treballar() { /* treballa */ }
    public void menjar() { /* menja */ }
}
```

📌 **Solució:** Ara cada classe només implementa els mètodes que realment necessita.

***

### **D - Dependency Inversion Principle (DIP)**

Les classes han de dependre d’abstraccions (interfícies), no de classes concretes.

🔹 **Benefici:** Millora la flexibilitat i facilita la substitució de dependències.

**❌ Exemple incorrecte:**

```java
class Teclat {} 
class Ordinador {
    private Teclat teclat = new Teclat();
}
```

📌 **Problema:** `Ordinador` està directament lligat a `Teclat`, dificultant-ne el canvi.

**✅ Exemple correcte (DIP aplicat):**

```java
interface DispositiuEntrada {}
class Teclat implements DispositiuEntrada {}
class Ratoli implements DispositiuEntrada {}

class Ordinador {
    private DispositiuEntrada dispositiu;
    Ordinador(DispositiuEntrada dispositiu) {
        this.dispositiu = dispositiu;
    }
}
```

📌 **Solució:** Ara `Ordinador` pot utilitzar qualsevol dispositiu d’entrada.
