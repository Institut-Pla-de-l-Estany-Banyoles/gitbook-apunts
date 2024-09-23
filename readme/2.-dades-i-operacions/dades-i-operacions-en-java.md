---
description: >-
  Veurem com es concreten aquests diferents elements amb el llenguatge de
  programació Java
---

# Dades i operacions en Java

### **Estructura d’un programa Java**

En Java, un programa està format per un o més fitxers que contenen classes. Cada classe pot tenir un punt d'entrada definit pel mètode `main()`. Aquest mètode és el primer que s'executa quan s'inicia el programa. L'estructura bàsica és:

```java
import java.util.*; // Llibreries que es poden importar si cal

class MevaClasse { // Definició d'una classe
    public static void main(String[] args) { // Mètode principal (punt d'entrada)
        // Aquí van les instruccions del programa
    }
}

```

Aquest codi defineix una classe anomenada `MevaClasse` amb el mètode `main` que és el punt d'entrada del programa.

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

{% tab title="Boleans" %}
| Tipus     | Mida  | Valors      |
| --------- | ----- | ----------- |
| `boolean` | 1 bit | Cert o Fals |
{% endtab %}

{% tab title="Caràcters" %}
<table><thead><tr><th width="160">Tipus</th><th width="165">Mida</th><th>Valor</th></tr></thead><tbody><tr><td><code>char</code></td><td>2 bytes</td><td>Un sol caràcter codificat en ANSII</td></tr></tbody></table>
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

**Aritmètics**: `+`, `-`, `*`, `/`, `%`

```java
int suma = 5 + 3;  // suma val 8
int residu = 5 % 2;  // residu val 1
```

