# Control d'excepcions

El control d'excepcions és un mecanisme que permet gestionar errors o condicions anòmales durant l'execució d'un programa. L'ús d'excepcions facilita la identificació d'errors i permet respondre adequadament a situacions imprevistes, evitant que el programa s'aturi inesperadament.

Una **excepció** és un esdeveniment que passa durant l'execució d'un programari, i que trenca el flux normal d'execució d'instruccions.

Quan hi ha una excepció, el mètode on passa crea un objecte (**excepció**) i la llença a l'entorn d'execució (**throws**). Aquest objecte indica què ha passat i quin era l'estat quan ha passat. L'objecte de l'excepció inclou la llista de mètodes que s'havia cridat quan passa l'excepció, o **call stack**.

L'entorn d'execució busca un bloc de codi que pugui **gestionar** l'excepció. Aquesta cerca es fa des del mètode on es produeix l'excepció i en ordre invers de crida, fins a arribar al mètode **main**. Quan es troba el codi que gestiona l'excepció (**catch**), l'entorn d'execució passa l'excepció al codi corresponent. Si no en troba cap, el programa acaba.

#### Avantatges de les excepcions:

* Permeten separar el codi de gestió d'errors del codi normal.
* Permeten propagar els errors, tenint un punt comú per gestionar errors d'un cert tipus.
* Permet agrupar i diferenciar tipus d'errors, utilitzant gestors més o menys generals.

### Tipus d'excepcions

Java disposa de diferents tipus d'excepcions, entre les quals destaquen:

* **Excepcions controlades** (Checked Exceptions): Excepcions que s'han de gestionar obligatòriament. Exemples: `IOException`, `SQLException`.
* **Excepcions no controlades** (Unchecked Exceptions): No és necessari gestionar-les explícitament. Exemples: `ArithmeticException`, `NullPointerException`.
* **Errors**: Són problemes greus que generalment no es poden gestionar, com els errors de memòria (`OutOfMemoryError`).

***

### Bloc `try-catch`

#### Descripció

El bloc `try` s'utilitza per a envoltar el codi que pot generar una excepció. Si es produeix una excepció dins del bloc `try`, s'executa el bloc `catch` corresponent, que conté el codi per gestionar l'error.

#### Sintaxi

```java
try {
    // Codi que pot llançar una excepció
} catch (ExcepcioType e) {
    // Codi per gestionar l'excepció
}
```

#### Exemple

En aquest exemple es captura una divisió per zero fent servir `ArithmeticException`.

```java
try {
    int resultat = 10 / 0;  // Això genera una ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Error: No es pot dividir per zero.");
}
```

**Sortida:**

```yaml
Error: No es pot dividir per zero.
```

#### Explicació

* Si es produeix una divisió per zero, el bloc `catch` captura l'excepció `ArithmeticException` i mostra un missatge d'error.
* Si no es produeix cap error, el bloc `catch` s'ignora.

***

### Bloc `try-catch-finally`

#### Descripció

El bloc `finally` s'executa sempre després dels blocs `try` i `catch`, tant si es produeix una excepció com si no. És útil per efectuar operacions de neteja, com tancar fitxers o alliberar recursos.

#### Sintaxi

```java
try {
    // Codi que pot llançar una excepció
} catch (ExcepcioType e) {
    // Codi per gestionar l'excepció
} finally {
    // Codi que s'executa sempre
}
```

#### Exemple

Aquest exemple inclou un bloc `finally` per assegurar-se que es mostra un missatge al final.

```java
try {
    int resultat = 10 / 0;  // Genera una ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Error: No es pot dividir per zero.");
} finally {
    System.out.println("Finalització de l'operació.");
}
```

**Sortida:**

```yaml
Error: No es pot dividir per zero.
Finalització de l'operació.
```

#### Explicació

* El bloc `catch` captura l'excepció i mostra el missatge d'error.
* El bloc `finally` s'executa sempre, independentment de si es produeix una excepció.

***

### Llançament d'excepcions amb `throw`

#### Descripció

L'operador `throw` s'utilitza per llançar una excepció de manera explícita. És útil per indicar errors o situacions específiques dins d'un programa.

#### Sintaxi

```java
if (condicio) {
    throw new ExcepcioType("Missatge d'error");
}
```

#### Exemple

Aquest exemple llança una `IllegalArgumentException` si el valor d'entrada és negatiu. L'acció _establirEdat_, veurem més endavant **accions i funcions**, en cas que se li faciliti una edat negativa, llença una excepció que l'argument  rebut no és vàlid.

```java
public void establirEdat(int edat) {
    if (edat < 0) {
        throw new IllegalArgumentException("L'edat no pot ser negativa.");
    }
    System.out.println("L'edat és: " + edat);
}
```

**Ús:**

```java
try {
    establirEdat(-5);  // Llança una excepció
} catch (IllegalArgumentException e) {
    System.out.println("Excepció: " + e.getMessage());
}
```

**Sortida:**

```yaml
Excepció: L'edat no pot ser negativa.
```

#### Explicació

* Quan `edat` és negatiu, es llança una `IllegalArgumentException` amb un missatge personalitzat.
* El bloc `catch` captura l'excepció i mostra el missatge.

***

### Resum dels elements del control d'excepcions

| Bloc      | Funció                                                        |
| --------- | ------------------------------------------------------------- |
| `try`     | Envolta el codi que pot generar una excepció.                 |
| `catch`   | Gestiona l'excepció si es produeix dins del bloc `try`.       |
| `finally` | S'executa sempre, tant si es produeix una excepció com si no. |
| `throw`   | Llança una excepció explícita.                                |
