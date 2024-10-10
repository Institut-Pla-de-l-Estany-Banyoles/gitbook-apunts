# Tipus de dades

La representació de les dades que poden necessitar pels nostres programes és molt diversa, és per això que tenim diferents tipus de dades per tal de poder-les representar. La codificació i espai que ocupin aquestes dades, pot variar en funció del llenguatge de programació i el sistema operatiu, però sí que hi ha un conveni amb els principals tipus de dades necessaris i la majoria dels llenguatges els incorporen.&#x20;

#### **Dades numèriques**

* **Enter**: Es fan servir per treballar amb nombres sencers, com `34`, `-15`, o `0`.
* **Real**: Representen nombres amb decimals, com `3.14` o `-12.5`.

#### **Dades no numèriques**

* **Caràcter**: Un únic símbol, com `'A'`, `'5'`, o `'#'`.
* **Booleà**: Pot tenir dos valors, `cert` o `fals`, usats per gestionar condicions lògiques.

***

### **Tipus de dades en Java**

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

{% hint style="info" %}
Com hem vist a l'apartat anterior, la declaració i inicialització de les variables segueixen el patró:

<mark style="color:red;">tipusVariable</mark> nomVariable = <mark style="color:blue;">valorInicialització</mark>;

<mark style="color:red;">tipusVariable</mark> nomVariable2;\
nomVariable2 = <mark style="color:blue;">valorInicialització</mark>;    &#x20;
{% endhint %}

