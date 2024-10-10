# Operadors

A l'apartat anterior hem vist els diferents tipus de dades que podem disposar, però de poc servirien si no hi podem operar. És per això que existeixen diferents operacions que podem realitzar amb aquestes. La implementació d'aquestes operacions dependrà del llenguatge de programació.

* **Aritmètics**: S'utilitzen per efectuar operacions matemàtiques bàsiques:
  * `+` (suma), `-` (resta), `*` (producte), `/` (divisió), `%` (mòdul o residu).
* **Relacionals**: Comparen dos valors:
  * `==` (igual), `!=` (diferent), `<`, `<=`, `>`, `>=`.
* **Lògics**: Treballen amb valors booleans:
  * `&&` (AND), `||` (OR), `!` (NOT).

***

### Operadors en Java

Els operadors s'utilitzen per efectuar càlculs, operacions o comparacions entre diferents valors.&#x20;

#### **Aritmètics**: `+`, `-`, `*`, `/`, `%`, `++`, `--`

```java
//Aquests operadors ens permeten realitzar operacions matemàtiques
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

Els operadors relacionals sempre donen com a resultat de la seva avaluació o execució un booleà. Per tant, el resultat d'una operació relacional sempre serà `true` o `false`.

```java
// Aquest operadors ens permeten comparar elements
int a = 5;
int b = 3;

// Operadors relacionals
boolean esMajor = a > b;    // esMajor val true, ja que 5 és més gran que 3
boolean esMenor = a < b;    // esMenor val false, ja que 5 no és més petit que 3
boolean esIgual = a == b;   // esIgual val false, ja que 5 no és igual a 3
boolean noEsIgual = a != b; // noEsIgual val true, ja que 5 no és igual a 3
boolean esMajorIgual = a >= b; // esMajorIgual val true, ja que 5 és més gran o igual que 3
boolean esMenorIgual = a <= b; // esMenorIgual val false, ja que 5 no és més petit ni igual que 3

```

#### Lògics: `&&`, `||`, `!`

```java
// Aquests operadors ens permeten realitzar operacions lògiques
boolean veritat = true;
boolean fals = false;

// Operador AND (&&): tots dos valors han de ser true perquè el resultat sigui true
boolean resultatAnd = veritat && fals;  // resultatAnd val false, ja que una de les condicions és false

// Operador OR (||): almenys un valor ha de ser true perquè el resultat sigui true
boolean resultatOr = veritat || fals;   // resultatOr val true, ja que almenys una de les condicions és true

// Operador NOT (!): inverteix el valor de la condició
boolean negacio = !veritat;             // negacio val false, ja que inverteix el valor de veritat (true)

boolean combinacio = (veritat || fals) && !fals;  // combinacio val true, perquè "veritat OR fals" dona true i "NOT fals" dona true


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
