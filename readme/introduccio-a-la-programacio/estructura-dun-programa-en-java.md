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

### Comentaris

El codi font d'un programa no només conté instruccions per ser executades, també inclouen els comentaris. Aquests permeten als programadors documentar el codi. Aquestes línies no s'executen, només serveixen per afegir explicacions o documentació dins del codi.

1. Comentaris de línia `//`
   * Per fer comentaris breus que expliquen una sola línia o instrucció de codi.
   * És útil per documentar petites accions o passos dins d'un mètode.
2. Comentaris de bloc `/*  */`
   * Per fer comentaris més extensos que expliquen seccions completes de codi.
   * Ideal per descriure mètodes, funcions o blocs de lògica complexa.
3. Comentaris de documentació `/** */`
   * Per documentar classes, mètodes o atributs de manera detallada.
   * Permet generar documentació HTML automàtica mitjançant eines com **Javadoc**.
   * Pot incloure etiquetes especials com `@param` o `@return` per descriure els paràmetres i els valors de retorn.
