# Cadenes de Caràcters (String)

Un **`String`** és una seqüència de caràcters que representa text. És una classe especial que forma part del paquet `java.lang` i es tracta com un tipus immutable. Això vol dir que un cop creat, el contingut d’un objecte `String` **no es pot modificar**.

Els objectes `String` són molt utilitzats en Java per emmagatzemar i manipular text, ja sigui per a operacions simples com concatenar cadenes o per a operacions més complexes com cerques i substitucions.

<figure><img src="../../.gitbook/assets/image (12).png" alt="" width="375"><figcaption></figcaption></figure>

#### Creació directa

```java
// Creació i inicialitació amb literal d'una línia
String salutacio = "Hola, món!";

// A partir de Java 15, podem inicialitzar amb "Text BLock" fent servir les triple "
// és interessant ja que manté el format del text original.
String blocText = """
    Hola, món!
    Aquest és un bloc de text.
    Formatat de manera natural.
    """;

//Creació mitjançant el constructor
String salutacio = new String("Hola, món!");

//Creació a partir d'un array de caràcters
char[] lletres = {'H', 'o', 'l', 'a'};
String paraula = new String(lletres);
```

#### Principals mètodes

En tractar-se d'objectes, les cadenes de text tenen un conjunt de mètodes associats per poder treballar amb elles. Anem a veure els principals.

Podeu consultar la [documentació oficial de la classe String de Java 21 ](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/String.html)per veure tots els mètodes i constructors.

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Mètode</strong></td><td><strong>Ús</strong></td><td><strong>Descripció</strong></td></tr><tr><td><code>length()</code></td><td><code>cadena.length()</code></td><td>Retorna la longitud de la cadena.</td></tr><tr><td><code>equals(Object obj)</code></td><td><code>cadena1.equals(cadena2)</code></td><td>Compara si dues cadenes són iguals (distingeix majúscules i minúscules).</td></tr><tr><td><code>compareTo(String anotherStr)</code></td><td><code>cadena1.compareTo(cadena2)</code></td><td>Compara lexicogràficament dues cadenes. Retorna 0 si són iguals, un valor negatiu si <code>cadena1</code> és menor, i un valor positiu si <code>cadena1</code> és major.</td></tr><tr><td><code>charAt(int index)</code></td><td><code>cadena.charAt(2)</code></td><td>Retorna el caràcter en la posició especificada.</td></tr><tr><td><code>substring(int beginIndex)</code></td><td><code>cadena.substring(3)</code></td><td>Retorna una subcadena des de l'índex indicat fins al final de la cadena.</td></tr><tr><td><code>substring(int begin, int end)</code></td><td><code>cadena.substring(1, 4)</code></td><td>Retorna una subcadena des de l'índex <code>begin</code> fins a l'índex <code>end - 1</code>.</td></tr><tr><td><code>equalsIgnoreCase(String str)</code></td><td><code>cadena1.equalsIgnoreCase(cadena2)</code></td><td>Compara si dues cadenes són iguals sense distingir majúscules i minúscules.</td></tr><tr><td><code>toUpperCase()</code></td><td><code>cadena.toUpperCase()</code></td><td>Converteix tots els caràcters de la cadena a majúscules.</td></tr><tr><td><code>toLowerCase()</code></td><td><code>cadena.toLowerCase()</code></td><td>Converteix tots els caràcters de la cadena a minúscules.</td></tr><tr><td><code>trim()</code></td><td><code>cadena.trim()</code></td><td>Elimina els espais en blanc del principi i del final de la cadena.</td></tr><tr><td><code>replace(char old, char new)</code></td><td><code>cadena.replace('a', 'o')</code></td><td>Substitueix totes les ocurrències d’un caràcter per un altre.</td></tr><tr><td><code>contains(CharSequence s)</code></td><td><code>cadena.contains("Hola")</code></td><td>Retorna <code>true</code> si la cadena conté la subcadena especificada.</td></tr><tr><td><code>indexOf(String str)</code></td><td><code>cadena.indexOf("a")</code></td><td>Retorna l'índex de la primera ocurrència d'una subcadena o caràcter (o -1 si no existeix).</td></tr><tr><td><code>split(String regex)</code></td><td><code>cadena.split(" ")</code></td><td>Divideix la cadena en parts segons el delimitador especificat (retorna un array).</td></tr><tr><td><code>startsWith(String prefix)</code></td><td><code>cadena.startsWith("Hola")</code></td><td>Retorna <code>true</code> si la cadena comença amb el prefix indicat.</td></tr><tr><td><code>endsWith(String suffix)</code></td><td><code>cadena.endsWith("món!")</code></td><td>Retorna <code>true</code> si la cadena acaba amb el sufix indicat.</td></tr></tbody></table>

#### Exemples d'ús

{% code fullWidth="true" %}
```java
public class ExempleString {
    public static void main(String[] args) {
    
        // Declaració de la cadena inicial
        String text = "Hola, món!";
        String cadena1 = "Hola";
        String cadena2 = "hola";

        // length()
        System.out.println("Longitud de la cadena: " + text.length()); // Sortida: 10

        // equals(Object obj)
        System.out.println("Són iguals? " + cadena1.equals(cadena2)); // Sortida: false
        System.out.println("Són iguals exactament? " + cadena1.equals("Hola")); // Sortida: true

        // compareTo(String anotherStr)
        System.out.println("Comparació lexicogràfica (cadena1 > cadena2): " + cadena1.compareTo(cadena2)); //Sortida: -32
        System.out.println("Comparació lexicogràfica (cadena2 < cadena1): " + cadena2.compareTo(cadena1)); //Sortida: 32

        // charAt(int index)
        System.out.println("Caràcter a la posició 5: " + text.charAt(5)); // Sortida: m

        // substring(int beginIndex)
        System.out.println("Subcadena des de la posició 6: " + text.substring(6)); // Sortida: món!

        // substring(int beginIndex, int endIndex)
        System.out.println("Subcadena des de la posició 6 a la 9: " + text.substring(6, 9)); // Sortida: món

        // equalsIgnoreCase(String str)
        System.out.println("Són iguals sense distingir majúscules/minúscules? " + cadena1.equalsIgnoreCase(cadena2)); // Sortida: true

        // toUpperCase()
        System.out.println("En majúscules: " + text.toUpperCase()); // Sortida: HOLA, MÓN!

        // toLowerCase()
        System.out.println("En minúscules: " + text.toLowerCase()); // Sortida: hola, món!

        // trim()
        String textAmbEspais = "   Hola, món!   ";
        System.out.println("Sense espais: '" + textAmbEspais.trim() + "'"); // Sortida: 'Hola, món!'

        // replace(char oldChar, char newChar)
        System.out.println("Substitueix 'o' per 'a': " + text.replace('o', 'a')); // Sortida: Hala, món!

        // contains(CharSequence s)
        System.out.println("Conté 'món'? " + text.contains("món")); // Sortida: true

        // indexOf(String str)
        System.out.println("Índex de la primera 'o': " + text.indexOf("o")); // Sortida: 1

        // split(String regex)
        String[] parts = text.split(", ");
        System.out.println("Primera part: " + parts[0]); // Sortida: Hola
        System.out.println("Segona part: " + parts[1]); // Sortida: món!
    }
}

```
{% endcode %}

### Notes sobre la Immutabilitat

Els objectes de tipus `String` són **immutables**:

* Quan es modifica una cadena, en realitat es crea un nou objecte en memòria.
* Això pot tenir impacte en el rendiment si s'efectuen moltes operacions amb cadenes. Per optimitzar, es recomana utilitzar **`StringBuilder`** o **`StringBuffer`** per manipular cadenes dinàmicament.

Exemple amb `StringBuilder`

```java
StringBuilder sb = new StringBuilder("Hola");
sb.append(", món!");
System.out.println(sb.toString()); // Sortida: Hola, món!
```

#### Caràcters d'escapament

Ja hem anat veient diferents caràcters d'escapament mentre hem fet ús del mètode printf, aprofitem aquí que parlem de nou de les cadenes de caràcters per recopilar els principals.

| Seqüència d'Escapament | Descripció                        | Exemple                           | Sortida              |
| ---------------------- | --------------------------------- | --------------------------------- | -------------------- |
| `\n`                   | Salt de línia                     | `"Hola,\nMón!"`                   | <p>Hola,<br>Món!</p> |
| `\t`                   | Tabulador                         | `"Hola,\tMón!"`                   | Hola, Món!           |
| `\"`                   | Cometes dobles dins del `String`  | `"Ell va dir: \"Hola!\""`         | Ell va dir: "Hola!"  |
| `\'`                   | Cometes simples dins del `String` | `"És un caràcter: \'A\'"`         | És un caràcter: 'A'  |
| `\\`                   | Barra invertida (`\`)             | `"C:\\Usuari\\Document"`          | C:\Usuari\Document   |
| `\r`                   | Retorn de carro (carriage return) | `"Hola,\rMón!"`                   | Món!                 |
| `\b`                   | Retrocedir un espai (backspace)   | `"ABC\bD"`                        | ABD                  |
| `\f`                   | Salt de pàgina (form feed)        | `System.out.print("Hola\fMón!");` | (depèn del terminal) |
| `\uXXXX`               | Caràcter Unicode, com un emoji 😊 | `"\u263A"`                        | ☺                    |

