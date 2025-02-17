# Definir classes

Tot fitxer de codi font amb Java és una classe. Qualsevol fitxer .java és una classe. Podem distingir quatre parts principals en les classes. Els atributs, els constructors, els mètodes de consulta i modificació (getters i setters) i els mètodes d'objecte o de classe.

<figure><img src="../../.gitbook/assets/image (4) (2).png" alt=""><figcaption></figcaption></figure>

### **Atributs (Propietats o Camps)**

Els **atributs** són les propietats o característiques de l'objecte. Representen l'estat de cada instància de la classe.

#### **Característiques**

* Representen **dades** relacionades amb l'objecte.
* Haurien de ser **privats** (`private`) per evitar modificacions no controlades.
* Se solen inicialitzar dins del **constructor** o mitjançant **mètodes setters**.

#### 📌 **Exemple de codi**

```java
public class Persona {

    private String nom;
    private int edat;
}
```

{% hint style="warning" %}
**Per què els atributs han de ser `private`?**

* Per aplicar **encapsulació**, impedint que es modifiquin directament des de fora de la classe.
* **Controlar la modificació** d'aquests a partir dels mètodes setter
* L'accés es fa a través de **mètodes getters i setters**.
{% endhint %}

***

### **Constructors**

Els **constructors** són mètodes especials que s'executen quan es crea un objecte i s'encarreguen d'inicialitzar els seus atributs. En funció de les necessitats poden haver-hi diferents constructors.

#### **Característiques**

* Tenen **el mateix nom que la classe**.
* No tenen **tipus de retorn** (ni `void` ni cap altre).
* Poden tenir **paràmetres** per assignar valors als atributs de l'objecte.
* Pot haver-hi **més d'un constructor** sempre que tinguin diferents paràmetres. La **sobrecàrrega de constructors** permet crear objectes de diferents maneres.

#### 📌 **Exemple de codi**

```java
// Constructor per defecte (si no en definim cap, Java el crea automàticament)
// En el cas que el crees Java automàticament, els camps s'inicialitzarien amb els valors per defecte
// null en el cas de String i 0 en el cas de int
public Persona() {
    this.nom = "Sense nom";
    this.edat = 0;
}

// Constructor amb paràmetres (per inicialitzar atributs)
// Poden no exposar-se o no permetre inicialitzar tots els atributs que realment té la classe.
public Persona(String nom, int edat) {
    this.nom = nom;
    this.edat = edat;
}

// Constructor còpia (copia els atributs d'un altre objecte Persona rebut com a paràmetre)
public Persona(Persona altraPersona) {
    this.nom = altraPersona.nom;
    this.edat = altraPersona.edat;
}
```

{% hint style="danger" %}
És important garantir que quan es crea un objecte, tots els seus camps quedin inicialitzats. Si no es fa, podria resultar amb excepcions tipus NullPointerException
{% endhint %}

***

### **Getters i Setters**

Els **mètodes getter i setter** s’utilitzen per **accedir i modificar** els atributs d'una classe de manera controlada.

#### **Per a què s'utilitzen?**

* **Encapsulació**: Eviten l'accés directe als atributs (`private`).
* **Seguretat**: Permeten validar dades abans de modificar-les.
* **Modificació controlada**: Es poden establir restriccions a certs atributs.

#### 📌 **Exemple de codi**

```java
public String getNom() {
    return nom;
}

public void setNom(String nom) {
    this.nom = nom;
}

public int getEdat() {
    return edat;
}

public void setEdat(int edat) {
    this.edat = edat;
}
```

:bulb:En el cas de les propietats tipus `boolean`, els seus mètodes de consulta i accés són `is` i `set`. Posem per cas que una _Assignatura_ o un _Alumne_ tenen una propietat de tipus booleà anomenada aprovat. En aquest cas, per consultar el seu estat seria _isAprovat()_ i per assignar-li un valor `setAprovat(true)`

{% hint style="warning" %}
**Per a què són importants els mètodes `setter`?**

* Permeten aplicar validacions (per exemple, evitar edats negatives).
* Protegeixen els atributs de modificacions incorrectes.
{% endhint %}

***

### Mètodes de Classe i d'Objecte

Els **mètodes** són accions que un objecte pot realitzar, és a dir, què pot fer.

Característiques

* Poden **modificar** l'estat de l'objecte que els invoca
* Poden o no **retornar** informació
*   Poden ser de Classe (`static`) o d'Objecte

    * **D'objecte**: necessiten una instància de la classe (un objecte) per ser cridat

    <figure><img src="../../.gitbook/assets/image (3) (2).png" alt=""><figcaption></figcaption></figure>

    * **De classe:** es defineixen amb la paraula clau `static`, per invocar-los s'ha d'utilitzar el nom de la classe.

    <figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

#### 📌 **Exemple de codi**

```java
public void saluda(){
    System.out.printf("Hola, em dic %s i tinc %d anys \n", nom, edat);
}
```

***

### **Resum**

| **Atributs**                     | Emmagatzemen les dades de l'objecte.                         |
| -------------------------------- | ------------------------------------------------------------ |
| **Constructor**                  | Inicialitza els atributs quan es crea l'objecte.             |
| **Getters**                      | Retornen el valor d'un atribut.                              |
| **Setters**                      | Modifiquen el valor d'un atribut de manera controlada.       |
| **Mètodes d'Objecte**            | Defineixen accions que l'objecte pot realitzar.              |
| **Mètodes de Classe (`static`)** | Són funcions generals que no depenen d'un objecte específic. |
