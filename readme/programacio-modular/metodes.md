# Mètodes

### Què són els Mètodes?

{% embed url="https://www.youtube.com/watch?t=&v=K5IELYVaGlc" %}

Un **mètode** és un bloc de codi amb un nom identificador que es pot cridar per executar una tasca específica. Els mètodes ajuden a dividir un programa en petites unitats lògiques.

Podem distingir dos tipus de mètodes segons si retornen o no informació després de la seva execució. Les **accions** i les **funcions**.

**Acció (Procediment):**

* És un mètode que **no retorna cap valor**.
* Executa una tasca específica, com mostrar missatges a la consola.
* En Java, s'identifica amb el tipus de retorn `void`.

**Funció:**

* És un mètode que **retorna un valor**.
* Sempre té un tipus de retorn (com `int`, `double`, `String`...).
* S'utilitza sovint per càlculs o per retornar informació.

***

### Definir un mètode

Un mètode es defineix seguint aquesta estructura:

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Definició d'un mètode</p></figcaption></figure>

```markup
[modificador] [tipus de retorn] nomMètode([paràmetres]) {
    // cos del mètode
}
```

#### Components d'un Mètode

1. **Modificador:** Defineix la visibilitat (`public`, `protected` o`private`) i altres propietats com si el mètode és estàtic o no `static`
2. **Tipus de retorn:** Especifica el tipus del valor que retorna el mètode (per exemple, `int`, `double`, `String`..., o `void` **si no retorna res**).
3. **Nom del mètode:** Identifica el mètode i segueix les convencions de noms en Java (notació camelCase).
4. **Paràmetres (opcionals):** Variables que el mètode pot rebre com a entrada.
5. **Cos del mètode:** Conté les instruccions que s'executaran quan es cridi el mètode.

#### Exemple:

```java
public static int suma(int a, int b) {
    return a + b;
}
```

***

### Com invocar o cridar un mètode

Per poder executar un mètode definit en el nostre programa l'hem de cridar. Un mètode es crida pel seu nom. Si té paràmetres, s'han de proporcionar en l'ordre correcte.

#### Exemple:

```java
public static void main(String[] args) {
    int resultat = suma(5, 3); // Crida del mètode definit anteriorment
    System.out.println("Resultat: " + resultat);
}
```

***

### Paràmetres i Arguments

* **Paràmetres:** Són les variables definides entre parèntesis a la declaració del mètode.
* **Arguments:** Són els valors proporcionats al mètode en el moment de la invocació.

#### Exemple:

```java
public static void mostrarMissatge(String missatge) { // Paràmetre
    System.out.println(missatge);
}

public static void main(String[] args) {
    mostrarMissatge("Hola, món!"); // Argument
}
```

***

### Retorn de Valors

Els mètodes poden retornar valors utilitzant la paraula clau `return`. Els mètodes que retornen informació, els anomenem **funcions**.&#x20;

#### Exemple:

```java
public static int quadrat(int numero) {
    return numero * numero;
}
```

#### Nota:

Si el mètode no retorna cap valor, simplement realitza una acció, s'utilitza `void` com a tipus de retorn a la capçalera del mètode. En aquest cas, els mètodes que realitzen un procediment, però no retornen cap informació els anomenem **acció.**

***

### Exemple Complet: Calculadora modular

```java
public class Calculadora {
    public static int suma(int a, int b) {
        return a + b;
    }

    public static int resta(int a, int b) {
        return a - b;
    }

    public static int multiplicacio(int a, int b) {
        return a * b;
    }

    public static double divisio(int a, int b) {
        if (b == 0) {
            System.out.println("Error: Divisió per zero.");
            return 0;
        }
        return (double) a / b;
    }

    public static void main(String[] args) {
        System.out.println("Suma: " + suma(10, 5));
        System.out.println("Resta: " + resta(10, 5));
        System.out.println("Multiplicació: " + multiplicacio(10, 5));
        System.out.println("Divisió: " + divisio(10, 5));
    }
}
```

**Sortida:**

```makefile
Suma: 15
Resta: 5
Multiplicació: 50
Divisió: 2.0
```

***
