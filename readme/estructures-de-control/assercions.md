# Assercions

Les **assercions** són una eina per fer comprovacions en el codi **durant el desenvolupament**. S'utilitzen per verificar condicions que, si són falses, indiquen un error en la lògica del programa. Les assercions són especialment útils per a proves i depuració, ja que ajuden a identificar errors de manera precoç.

#### Exemple

Posem per cas que tenim una variable que ens controla l'estoc d'un producte. Cada vegada que venem un producte, l'estoc es decrementarà en un. Després de fer aquesta operació, podríem posar una asserció que si l'estoc fos que l'estoc ha de ser més gran o igual que zero. En cas que aquesta pressuposició que s'ha de complir fos falsa, ens saltaria un error d'asserció indicant que l'estoc no pot ser inferior a 0. Això ens permetria revisar el nostre codi i depurar el lloc on no estem controlant aquesta situació.

***

### Què és una `Assertion`?

Una **`assertion`** és una expressió que comprova una condició booleana. Si la condició és certa, el programa continua l'execució normalment. Si la condició és falsa, es llança un error d'asserció (`AssertionError`) que indica un problema en el codi.

#### Sintaxi

```java
assert condicio : missatge;
```

* **`condicio`**: Una expressió booleana que ha de ser certa perquè el programa continuï.
* **`missatge`** _(opcional)_: Un missatge que es mostra si l'asserció falla.

#### Exemple

Aquest exemple mostra una asserció que comprova si una variable és positiva.

```java
int valor = -5;
assert valor >= 0 : "El valor ha de ser positiu!";
```

* Si `valor` és menor que zero, es llança una `AssertionError` amb el missatge `"El valor ha de ser positiu!"`.

***

### Ús d'assercions: Bones pràctiques

#### 3.1 Verificació de condicions que no han de fallar

Les assercions són útils per verificar condicions internes del programa que **no haurien de fallar** si la lògica és correcta.

**Exemple:**

```java
int edat = obtenirEdat();
assert edat >= 0 : "L'edat no pot ser negativa!";
```

En aquest exemple, s'usa una assertion per verificar que l'edat no sigui negativa, una condició que, en teoria, no hauria de fallar.

#### 3.2 No utilitzar assertions per gestionar errors d'usuari o validar dades externes

Les assertions no són adequades per a gestionar errors que es produeixin a causa de dades proporcionades per l'usuari o per validar dades d'entrada externes. S'utilitzen exclusivament per condicions internes del codi.

**Exemple (mala pràctica):**

```java
// No és recomanable utilitzar assertions per validar dades d'usuari.
assert nomUsuari != null : "El nom d'usuari no pot ser null!";
```

#### 3.3 Assertions amb condicions lògiques complexes

Les assertions poden combinar condicions lògiques complexes per assegurar-se que múltiples condicions són certes.

**Exemple:**

```java
int altura = 180;
int amplada = 100;
assert altura > 0 && amplada > 0 : "L'altura i l'amplada han de ser positives!";
```

En aquest exemple, l'assertion comprova que tant `altura` com `amplada` són positives.

***

### Llançament d'Errors d'Assertion

Quan una assertion falla (és a dir, quan la condició de l'assertion és `false`), es llança un `AssertionError`. Aquest error inclou el missatge d'error opcional que ajuda a identificar la causa del problema.

**Exemple amb missatge d'error personalitzat:**

```java
int resultat = calcularResultat();
assert resultat >= 0 : "El resultat ha de ser positiu, però és " + resultat;
```

Si `resultat` és negatiu, es llançarà un `AssertionError` amb el missatge especificat.

***

### Com activar les assercions

Les assercions estan **desactivades per defecte** en Java per evitar penalitzacions de rendiment en entorns de producció. Es poden activar en temps d'execució utilitzant l'opció de línia de comandes `-ea` (enable assertions).

#### Activar assertions en la línia de comandes:

```bash
java -ea NomPrograma
```

* Per desactivar les assercions, es pot fer servir l'opció `-da` (disable assertions), que és l'opció predeterminada.

#### Activar assertions a IntelliJ



{% stepper %}
{% step %}
Selecciona`Run` → `Edit Configurations...`
{% endstep %}

{% step %}
Selecciona la configuració d'execució en qüestió
{% endstep %}

{% step %}
Clica `Modify options` i selecciona `Add VM options`

<img src="../../.gitbook/assets/image (3) (1).png" alt="" data-size="original">
{% endstep %}

{% step %}
Afegeix`-ea` a `VM options`

<img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" data-size="original">
{% endstep %}
{% endstepper %}
