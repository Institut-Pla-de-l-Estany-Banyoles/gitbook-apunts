# Fitxers en Java

Podem utilitzar fitxers en un format a mida. Aquests són alguns possibles casos d'ús.

## Properties

Les [Properties](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Properties.html) són un format pla per a configuració d'una aplicació en format text. S'utilitzen parelles clau/valor que poden llegir-se (load) i escriure's (store).

## JSON

Podem escriure un arxiu de text en format [JSON](https://www.json.org/json-en.html), un format estructurat, i processar-lo utilitzant una de tantes llibreries existents. Per exemple, [JSON-java](https://github.com/stleary/JSON-java). Poden servir per llegir i persistir l'estat d'una aplicació, quan la quantitat de dades no és massa gran.

## YAML

YAML és un format d'entrada estructurat que també té algunes llibreries que permeten llegir-lo, com [snakeyaml](https://bitbucket.org/snakeyaml/snakeyaml/), però no està tan indicat per persistir.

## Arxius d'accés aleatori

Podem utilitzar [RandomAccessFile](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/RandomAccessFile.html) per a crear arxius binaris o de text amb registres de mida fixa. Això ens permet operar amb un índex sense haver de llegir tot l'arxiu com un stream. Hi ha utilitats a Java per exportar i importar tipus primitius utilitzant bytes, com [ByteBuffer](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/nio/ByteBuffer.html).

## Serialització

La serialització i la deserialització són processos que permeten convertir un objecte (Java) en un format fàcil de persistir i a la inversa.

El mecanisme de la JRE es basa en la utilització d'[ObjectInputStream](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/ObjectInputStream.html) i [ObjectOutputStream](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/ObjectOutputStream.html). Permeten utilitzar un stream per llegir i escriure objectes. Cal que l'objecte implementi [Serializable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/Serializable.html), i es pot fer serialització a mida implementat els mètodes privats writeObject i readObject.

Utilitzar els mecanismes Java de serializació pot fer que la nostra solució estigui tancada a altres llenguatges. Pot no ser un problema, si són arxius que no es compartiran fora.

JSON pot ser una solució de format més intercanviable. Les llibreries existents s'encarreguen de la serialització i deserialització.
