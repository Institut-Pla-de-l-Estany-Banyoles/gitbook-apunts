# Llibreries i paquets

### Llibreries (Library)

Una **llibreria** és una col·lecció de classes i interfícies que proporcionen funcionalitats reutilitzables. Aquestes funcionalitats poden ser tan bàsiques com les operacions matemàtiques o tan complexes com la connexió a una base de dades.

**Per a què utilitzem llibreries?**

{% hint style="info" %}
* **Reutilització de codi:** Evites escriure codi que ja existeix, cosa que estalvia temps i redueix errors.
* **Especialització:** Les llibreries estan dissenyades per a tasques específiques, proporcionant implementacions robustes i optimitzades.
* **Facilitat de desenvolupament:** Al proporcionar un conjunt de classes i mètodes predefinits, les llibreries simplifiquen el desenvolupament d'aplicacions.
{% endhint %}

***

Java ve equipat amb un conjunt robust de llibreries estàndard que proporcionen una àmplia gamma de funcionalitats, des de les més bàsiques fins a les més complexes. Aquestes llibreries són una part integral del **Java Development Kit (JDK)** i estan dissenyades per simplificar el desenvolupament d'aplicacions en Java.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>medium.com</p></figcaption></figure>

* **`java.lang`**
  * És la llibreria més bàsica i conté classes com `String`, `Math`, `Object`, etc.
  * S'utilitza per a operacions amb cadenes, càlculs matemàtics, manipulació d'objectes i altres tasques comunes.
* **`java.util`**
  * Proporciona col·leccions (llistes, conjunts, mapes), dates, aleatorietat, etc.
  * S'utilitza per a gestionar dades, treballar amb dates i hores, generar nombres aleatoris i altres tasques relacionades amb la utilitat.
* **`java.io`**
  * Proporciona classes per a entrada/sortida, com ara llegir i escriure fitxers, gestionar fluxos de dades, etc.
  * S'utilitza per a interactuar amb el sistema de fitxers, gestionar fluxos de dades de xarxa i altres operacions d'E/S.
* **`java.net`**
  * Proporciona classes per a xarxes, com ara sockets, URLs, etc.
  * S'utilitza per a desenvolupar aplicacions de xarxa, com ara clients i servidors.
* **`java.sql`**
  * Proporciona classes per a accedir a bases de dades relacionals.
  * S'utilitza per a connectar a bases de dades i executar consultes SQL.
* **`java.awt` i `javax.swing`**
  * Proporcionen classes per a crear interfícies gràfiques d'usuari (GUI).
  * S'utilitzen per a desenvolupar aplicacions amb interfícies gràfiques.

A part de les llibreries integrades en Java pels seus desenvolupadors, podem trobar i importar llibreries externes desenvolupades per altres empreses o comunitats de software lliure que ens obriran les portes a moltes altres funcionalitats.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p><a href="https://www.tatvasoft.com/outsourcing/2024/02/java-libraries.html">https://www.tatvasoft.com/outsourcing/2024/02/java-libraries.html</a></p></figcaption></figure>

### Paquets (Packages)

Un **paquet** en Java és un mecanisme per organitzar classes i interfaces en un jerarquia de directoris. Cada paquet té un nom únic que evita conflictes de noms entre classes de diferents paquets.

**Per a què utilitzem paquets?**

{% hint style="info" %}
* **Organització del codi:** Agrupa classes relacionades en paquets lògics, fent el codi més fàcil de gestionar i mantenir.
* **Espacios de nombres:** Evita conflictes de noms entre classes amb el mateix nom però en paquets diferents.
* **Control d'accés:** Els paquets permeten controlar l'accés a les classes i membres, afavorint l'encapsulament.
{% endhint %}

#### Relació entre Llibreries i Paquets

* **Les llibreries estan formades per paquets:** Una llibreria típica conté diversos paquets, cadascun amb un conjunt específic de classes i interfícies.
* **Els paquets proporcionen estructura a les llibreries:** La jerarquia de paquets ajuda a organitzar el codi dins d'una llibreria, facilitant la navegació i la comprensió.

#### Exemple

Imaginem una llibreria per treballar amb imatges. Aquesta llibreria podria contenir els següents paquets:

* **com.mycompany.image.io:** Conté classes per llegir i escriure imatges en diferents formats.
* **com.mycompany.image.processing:** Conté classes per realitzar operacions de processament d'imatges (escalat, rotacions, filtres, etc.).
* **com.mycompany.image.display:** Conté classes per mostrar imatges en una interfície gràfica.
