# Estructures de salt

Les estructures de control de salt permeten alterar el flux normal d'execució del programa. S'utilitzen per interrompre o saltar parts específiques d'un bloc de codi, sovint en bucles o en condicions específiques.

{% hint style="danger" %}
Les estructures de control de salt permeten alterar el flux normal d'execució d'un programa, però s'han d'utilitzar amb **prudència**. Quan s'abusen, poden fer que el codi sigui **més difícil de llegir i de mantenir** i compliquen el seguiment de la lògica del programa.

**Bones pràctiques:**

* Evita utilitzar estructures de salt quan sigui possible.
* Intenta resoldre el problema amb estructures alternatives (com `if` i `else`).
* Utilitza `break` i `continue` només quan millorin clarament la comprensió del codi.
{% endhint %}

### Estructura `break`

#### Descripció

La instrucció `break` s'usa per sortir immediatament d'un bucle (`for`, `while`, `do-while`) o d'un bloc `switch`. Quan es troba un `break`, el control del programa salta fora del bucle o del bloc `switch`, i l'execució continua amb la següent instrucció fora del bucle o bloc.

#### Sintaxi

```java
break;
```

#### Exemple en un bucle

Aquest exemple mostra com utilitzar `break` per sortir d'un bucle `for` quan es troba un nombre específic.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // Es surt del bucle quan i és 5
    }
    System.out.println("Número: " + i);
}
```

**Sortida:**

```makefile
Número: 1
Número: 2
Número: 3
Número: 4
```

***

### Estructura `continue`

#### Descripció

La instrucció `continue` es fa servir per saltar l'execució de la resta del codi en una iteració i passar directament a la següent iteració del bucle. És útil quan es vol ometre una part específica d'un bucle segons una condició, però sense aturar completament el bucle.

#### Sintaxi

```java
continue;
```

#### Exemple en un bucle

Aquest exemple mostra com utilitzar `continue` per saltar la impressió del número 5 dins d'un bucle `for`.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        continue; // Salta aquesta iteració quan i és 5
    }
    System.out.println("Número: " + i);
}
```

**Sortida:**

```makefile
Número: 1
Número: 2
Número: 3
Número: 4
Número: 6
Número: 7
Número: 8
Número: 9
Número: 10
```

***

### Estructura `return`

#### Descripció

La instrucció `return` s'usa per sortir d'un mètode i, opcionalment, retornar un valor. Quan es troba un `return`, l'execució del mètode es finalitza immediatament, i el control retorna al mètode que el va cridar.&#x20;

{% hint style="info" %}
Veurem més en detall aquesta instrucció quan comencem a treballar amb programació modular i l'ús de mètodes.
{% endhint %}

#### Sintaxi

```java
return;        
return valor;  // Per a mètodes que retornen un valor
```

#### Exemple en un mètode que retorna un valor

Aquest exemple mostra com utilitzar `return` per finalitzar un mètode i retornar el resultat d'una operació.

```java
public class ExempleReturn {
    
    //Mètode que donats dos valors enters a i b, retorna la seva multiplicació
    public static int multiplicar(int a, int b) {
        return a * b; // Retorna el resultat de multiplicar a per b
    }

    public static void main(String[] args) {
        int resultat = multiplicar(5, 3);
        System.out.println("El resultat és: " + resultat);
    }
}
```

**Sortida:**

```
El resultat és: 15
```

***

### Resum de les Estructures de Control de Salt

| Estructura | Funció                                                | Usos habituals                                             |
| ---------- | ----------------------------------------------------- | ---------------------------------------------------------- |
| `break`    | Finalitza un bucle o un bloc `switch`                 | Per sortir de bucles o `switch` abans del final            |
| `continue` | Salta a la següent iteració d'un bucle                | Per ometre una iteració segons una condició                |
| `return`   | Finalitza un mètode i, opcionalment, retorna un valor | Per retornar resultats o finalitzar l'execució d'un mètode |
