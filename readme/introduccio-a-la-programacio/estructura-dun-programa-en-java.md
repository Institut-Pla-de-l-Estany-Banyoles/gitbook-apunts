# Estructura d’un programa en Java

En aquest mòdul programarem fent servir el llenguatge Java, com ja hem vist a l'apartat anterior, aquest és un llenguatge híbrid.&#x20;

```
//TODO: WORA, JDK, JRE...
```

En Java, un programa està format per un o més fitxers que contenen classes. Cada classe pot tenir un punt d'entrada definit pel mètode `main()`. Aquest mètode és el primer que s'executa quan s'inicia el programa. L'estructura bàsica és:

{% code fullWidth="false" %}
```java
import java.util.*; // Llibreries que es poden importar si cal

class MevaClasse { // Definició d'una classe

    public static void main(String[] args) { // Mètode principal (punt d'entrada)
    
        // Aquí van les instruccions del programa
        // ...
        // ...
        
        System.out.println("Hello World!"); // Printa Hello World! per consola
    }
    
    // Aquí poden anar-hi més subprogrames definits per l'usuari (accions o funcions)
}
```
{% endcode %}

Aquest codi defineix una classe anomenada `MevaClasse` amb el mètode `main` que és el punt d'entrada del programa. Això ens permetrà començar a provar les nostres primeres línies de codi.
