# Excepcions

Una **excepció** és un esdeveniment que passa durant l'execució d'un programari, i que trenca el flux normal d'execució d'instruccions.

Quan hi ha una excepció, el mètode on passa crea un objecte (**excepció**) i la llença a l'entorn d'execució (**throws**). Aquest objecte indica què ha passat i quin era l'estat quan ha passat. L'objecte de l'excepció inclou la llista de mètodes que s'havia cridat quan passa l'excepció, o **call stack**.

L'entorn d'execució busca un bloc de codi que pugui **gestionar** l'excepció. Aquesta cerca es fa des del mètode on es produeix l'excepció i en ordre invers de crida, fins arribar al mètode **main**. Quan es troba el codi que gestiona l'excepció (**catch**), l'entorn d'execució passa l'excepció al codi corresponent. Si no troba cap, el programa acaba.

La gestió de l'excepció és apropiada si el tipus de l'excepció coincideix amb el de la gestió de l'excepció.

Avantatges de les excepcions:

* Permeten separar el codi de gestió d'errors del codi normal.
* Permeten propagar els errors, tenint un punt comú per gestionar errors d'un cert tipus.
* Permet agrupar i diferenciar tipus d'errors, utilitzant gestors més o menys generals.

## Referències

* [Compile and runtime errors in Java](https://introcs.cs.princeton.edu/java/11cheatsheet/errors.pdf)
* [Java Logging (Jenkov)](http://tutorials.jenkov.com/java-logging/index.html)
* [Java Logging Overview (Oracle)](https://docs.oracle.com/en/java/javase/11/core/java-logging-overview.html)
