---
description: >-
  Veurem com es concreten aquests diferents elements relacionats amb les dades i
  operacions amb el llenguatge de programació Java
hidden: true
---

# Dades i operacions en Java

### Variables&#x20;

Per poder a començar a utilitzar dades en els nostres programes, hem de **declarar les variables**. La declaració és la reserva d'aquell nom associat a un tipus de dada que serà. El tipus permet saber quant d'espai ha de reservar per emmagatzemar aquesta variable. La nomenclatura per fer-ho en Java és la següent:

&#x20;       <mark style="color:red;">tipusVariable</mark> nomVariable;

I no només això, per poder fer servir una variable, aquesta ha de tenir un **valor assignat**. Si intentem llegir el valor d'una variable a la qual mai se n'hi ha assignat un, ens trobarem amb un error. El primer cop que assignem un valor a una variable en diem inicialització. Ho podem fer juntament amb la declaració a la mateixa línia o a posteriori.

&#x20;        <mark style="color:red;">tipusVariable</mark> nomVariable = <mark style="color:blue;">valorInicialització</mark>;

Si ens ho imaginem de forma gràfica, la línia de codi <mark style="color:red;">`int`</mark>`age =`<mark style="color:blue;">`21`</mark>`;` acaba reservant un espai de memòria de 4 bytes (el que ocupa un `int`), associat al nom `age` i amb el valor `21` emmagatzemat en aquest espai de memòria.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="375"><figcaption><p>Declaració i inicialització d'una variable</p></figcaption></figure>

### **Tipus de dades**

Els tipus de dades en Java inclouen tant **tipus primitius** com **tipus referenciats.** Aquests últims els veurem en més detall més endavant.

#### **Tipus primitius**

{% tabs %}
{% tab title="Enters" %}
<table data-full-width="true"><thead><tr><th width="113">Tipus</th><th width="100">Mida</th><th>Valors</th></tr></thead><tbody><tr><td><code>byte</code></td><td>1 byte</td><td>-128 a 127</td></tr><tr><td><code>short</code></td><td>2 bytes</td><td>-32,768 a 32,767</td></tr><tr><td><code>int</code></td><td>4 bytes</td><td>-2,147,483,648 a 2,147,483,647</td></tr><tr><td><code>long</code></td><td>8 bytes</td><td> 9,223,372,036,854,775,808 a 9,223,372,036,854,775,807</td></tr></tbody></table>
{% endtab %}

{% tab title="Decimals" %}
<table><thead><tr><th width="114.66666666666666">Tipus</th><th width="103">Mida</th><th>Valors</th></tr></thead><tbody><tr><td><code>float</code></td><td>4 bytes</td><td>Un nombre de fins a 6 o 7 dígits decimals</td></tr><tr><td><code>double</code></td><td>8 bytes</td><td>Un nombre de fins a 15 dígits decimals</td></tr></tbody></table>
{% endtab %}

{% tab title="Caràcters" %}
<table><thead><tr><th width="160">Tipus</th><th width="165">Mida</th><th>Valor</th></tr></thead><tbody><tr><td><code>char</code></td><td>2 bytes</td><td>Un sol caràcter codificat en ANSII</td></tr></tbody></table>
{% endtab %}

{% tab title="Boleans" %}
| Tipus     | Mida  | Valors      |
| --------- | ----- | ----------- |
| `boolean` | 1 bit | Cert o Fals |
{% endtab %}
{% endtabs %}

#### Exemple

```java
int enter = 10;
float decimal = 3.14f;
boolean esVeritat = true;
char lletra = 'A';
```

### Operadors

Els operadors s'utilitzen per efectuar càlculs, operacions o comparacions entre diferents valors.&#x20;

#### **Aritmètics**: `+`, `-`, `*`, `/`, `%`, `++`, `--`

```java
int suma = 5 + 3;      // suma val 8
int resta = 3 - 2;     // resta val 1
int mult = 2 * 5;      // mult = 10
int div = 4 / 2;       // div = 2
int residu = 5 % 2;    // residu val 1

num--;                 // es redueix el valor de la variable num en 1
num++;                 // s'increment el valor de la vrialbe num en 1
```

Si volem operar sobre el valor que conté una variable i guardar-lo allà mateix, podem utilitzar els operadors `+=`, `-=`, `*=`, `/=` o `%=`.

```java
// Les dos operacions de cada una d'aquestes línies fa el mateix
suma = suma + 2;                    suma += 2;
resultat = resultat * 3             resultat *= 3;
```

#### Relacionals: `==`, `!=`, `<`, `<=`, `>`, `>=`

```java
// Aquest operadors ens permeten comparar elements
```

#### Lògics: `&&`, `||`, `!`

```java
// Aquests operadors ens permeten realitzar operacions lògica
```

#### Assignació: `=`

L'operador `=`, un de sol, és l'**operador d'assignació**. Aquest operador posar el valor de la dreta a la variable de l'esquerra.

L'hem vist a les 5 primeres operacions, assignem el contingut de la dreta de l'operador a la variable que tenim a l'esquerra. En el cas de `suma = 5 + 3;`, assignem a la variable suma, el resultat de fer l'operació de la dreta `5 + 3`.

***

#### Exemples

```java
public class Aritmetica {
    public static void main(String[] args) {
        int x = 10;
        int y = 20;
        
        int resultat = x + y;
        System.out.println("x + y = " + resultat);
        
        resultat = x - y;
        System.out.println("x - y = " + resultat);
        
        resultat = x * y;
        System.out.println("x * y = " + resultat);
        
        resultat = y / x;
        System.out.println("y / x = " + resultat);
        
        resultat = x % 3;
        System.out.println("x % 3 = " + resultat);
    }
}
```

<details>

<summary>Quina serà la sortida de l'execució del codi anterior? <span data-gb-custom-inline data-tag="emoji" data-code="1f914">🤔</span></summary>

```
x + y = 30 
x - y = -10
x * y = 200 
y / x = 2
x % 3 = 1
```

</details>
