# Estructures condicionals

Les estructures condicionals permeten executar diferents blocs d'instruccions depenent del valor d'una condició. Ens permeten prendre decisions en funció de valors, estats o diferents situacions que pugui prendre l'execució del programa. En Java, les principals estructures condicionals són: `if`, `if-else`, `else-if`, i `switch`.

### Estructura `if`

#### **Descripció**

La instrucció `if` avalua una condició booleana. Si aquesta condició és certa (`true`), s'executa el bloc de codi associat. Si és falsa, el bloc de codi s'ignora.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="330"><figcaption></figcaption></figure>

**Sintaxi**

```java
if (condicio) {
    // Bloc d'instruccions si la condició és certa
}
```

#### Exemple en Java

```java
int edat = 18;

if (edat >= 18) {
    System.out.println("Ets major d'edat.");
}
```

### Estructura `if-else`

#### **Descripció**

La instrucció `if-else` permet executar un bloc de codi si la condició és certa i un altre bloc si és falsa.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt="" width="342"><figcaption></figcaption></figure>

#### Sintaxi

```java
if (condicio) {
    // Bloc d'instruccions si la condició és certa
} else {
    // Bloc d'instruccions si la condició és falsa
}
```

{% hint style="info" %}
En Java també existeix l'oerador ternari. Ens permet fer un `if / else` de forma concisa en una sola línia. La seva sintaxis és la següent:

`nom_variable = (expressió) ? valor_si_cert : valor_si_fals ;` &#x20;
{% endhint %}

#### Exemple en Java

```java
int edat = 16;

if (edat >= 18) {
    System.out.println("Ets major d'edat.");
} else {
    System.out.println("Ets menor d'edat.");
}
```

L'exemple anterior utilitzat l'operador ternari seria així:

```java
int edat = 16;

String missatge = (edat >= 18) ? "Ets major d'edat." : "Ets menor d'edat.";

System.out.println(missastge);
```

### Estructura `if-else` en cascada

#### **Descripció**

La instrucció `if-else` en cascada ens permet executar un bloc de codi tenint en compte un conjunt de condicions.

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Sintaxi

```java
if (condicio) {
    // Bloc d'instruccions si la condició és certa
} else if (condicio2){
    // Bloc d'instruccions si la condició és falsa i la condicio2 és certa
} else if (condicio3){
    // Bloc d'instruccions si condició i condició2 són falces i condició3 és certa
} else {
    // Bloc d'instruccions si totes són falces
}
```

#### Exemple en Java

```java
int nota = 85; 

if (nota < 50) {
    System.out.println("Has suspès.");
} else if (nota >= 50 && nota < 70) {
    System.out.println("Tens un Bé.");
} else if (nota >= 70 && nota < 90) {
    System.out.println("Tens un Notable.");
} else if (nota >= 90) {
    System.out.println("Tens un Excel·lent.");
} else {
    System.out.println("Nota no vàlida.");
}
```

### Estructura `switch`

**Descripció**

La instrucció `switch` s’utilitza quan es vol comparar una expressió amb múltiples valors possibles. És una alternativa més llegible a la successió d’`if-else` que hem vist a l'apartat anterior.

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt="" width="398"><figcaption></figcaption></figure>

#### Sintaxi

```java
switch (expressio) {
    case valor1:
        // Bloc d'instruccions per valor1
        break;
    case valor2:
        // Bloc d'instruccions per valor2
        break;
    default:
        // Bloc d'instruccions per qualsevol altre valor
}
```

#### Exemple en Java

```java
int dia = 2;

switch (dia) {
    case 1:
        System.out.println("Dilluns");
        break;
    case 2:
        System.out.println("Dimarts");
        break;
    case 3:
        System.out.println("Dimecres");
        break;
    default:
        System.out.println("Un altre dia");
}
```

```java
// A partir de la versió Java 17 podem fer servir l'"Enhanced Switch" que millora la 
// llegibilitat de l'estructura i alguna funcionalitat més

int dia = 2;

switch (dia) {
    case 1 -> System.out.println("Dilluns");
    case 2 -> System.out.println("Dimarts");
    case 3 -> System.out.println("Dimecres");
    default -> System.out.println("Un altre dia");
}
```
