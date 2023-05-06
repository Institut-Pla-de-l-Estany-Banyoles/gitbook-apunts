# Persistència

## Localització de les dades

Una aplicació conté codi i dades. El codi interactua amb les dades que hi ha a la **memòria principal**, que és **volàtil**, el tipus de memòria més ràpida que existeix i la més senzilla de llegir i escriure. A POO, les dades són als objectes.

Un problema de la memòria principal és que perdem el seu contingut si l'aplicació finalitza, ja sigui de forma correcta o per un problema. El **context** necessari per a l'execució d'una aplicació és el seu **estat**, i cal recuperar-lo cada cop que les executem. Això es fa utilitzant **memòria no volàtil** basada en un o diversos arxius físics.

Quan parlem de recuperar el context d'una aplicació per a la seva execució, no sempre és possible fer-ho amb totes les dades que es gestionen. Pot ser perquè la mida sigui superior a la de la memòria principal, però també perquè no calgui i sigui millor ser mandrós en la seva càrrega per raó de rendiment.

## Model de dades

El disseny del model de dades ha de tenir en compte el millor rendiment possible quan s'utilitza memòria no volàtil, molt més lenta, i facilitar la futura escalabilitat de les nostres dades.

Un mecanisme per a minimitzar temps és la **memòria cache**: mantenim un nombre limitat d'objectes a la memòria principal per evitar haver-los de carregar des de la memòria no volàtil cada cop, i els invalidem si es modifiquen.

També els SGBD poden proporcionar-nos mecanismes per a processar les dades sense necessitat de carregar-les en memòria, gràcies a **llenguatges declaratius** com SQL: demanem quines dades necessitem, no com processar-les.

Si parlem de disseny, és convenient crear una capa de persistència que encapsuli el procés. Això ens permetrà substituir-la sense afectar la resta de l'aplicació. Si parlem d'usabilitat, la persistència hauria de ser transparent per a l'usuari.

## Què, quan i com persistir

Tenim dos mètodes de persistència: d'estat, el més habitual, i basat en esdeveniments.

### Persistència d'estat

Parlant de POO, ens podríem fer la pregunta de si allò que volem persistir és un objecte o una estructura de dades. Els objectes tenen comportament i encapsulen les dades. Les estructures de dades exposen les dades i no tenen comportament. Aquesta distinció ens ajudarà a decidir la nostra estratègia de persistència.

Per definir la persistència, cal repassar els camps de l'objecte i decidir quins necessitarem per tal de tornar a instanciar l'objecte en memòria principal. Alguns camps innecessaris poden ser calculats o tenir una funció temporal. Podem ajudar-nos de l'estudi dels constructors i setters de l'objecte.

A més, ens caldrà fer referències entre els objectes. Quan dissenyem mecanismes ad-hoc, podem utilitzar un [identificador d'objecte](https://en.wikipedia.org/wiki/Object\_identifier) en el moment de la persistència. En el cas dels SGBD, els objectes es relacionen amb claus foranes.

Tenim diversos àmbits de persistència:

* Context general de l'aplicació: configuracions generals, per usuari, etc.
* Documents, basats en serialització. Persistim en base a un document que pot intercanviar-se.
* Registres, habitualment relacionats i associats a SGBD. No se sol restaurar completament al començament, només quan cal.

### Persistència d'esdeveniments

La persistència per esdeveniments ([Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html)) és un mecanisme que permet restaurar l'estat d'una aplicació a partir de tots els esdeveniments que s'han produït. Es tracta d'una mena de log on es guarden els esdeveniments per ordre d'ocurrència, i que permet reconstruir l'estat en qualsevol moment del temps.

Quan l'aplicació s'inicia, reconstrueix l'estat actual aplicant tots els esdeveniments en l'ordre en que es val produir. Com que podria haver molts d'esdeveniments, aquest mecanisme se sol combinar amb altres, com per exemple emmagatzemar un estat intermedi (snapshot) i aplicar els esdeveniments a partir d'aquell instant.

### Quan i com

Hem de persistir sempre que hi hagi un canvi en alguna dada? La resposta general és que sí. Així evitem perdre dades si el nostre programa falla abans d'haver persistit. Però de vegades no seria òptim, parlant de rendiment, haver de persistir tot l'estat d'una aplicació. Alternativament, es podria endarrerir el moment, o fer-ho periòdicament de forma automàtica. També podem deixar aquesta responsabilitat en mans de l'usuari (File > Save).

La persistència per esdeveniments permet només guardar l'esdeveniment que es produeix en lloc de totes les dades, i també pot ser una solució per millorar el rendiment.

## Quin tipus de persistència?

El format i organització dependrà de les nostres necessitats.

**Criteris per decidir la forma de persistència**:

* És una aplicació monousuari o multiusuari?
* Es comparteix informació a la xarxa amb altres clients o aplicacions?
* Hi ha un volum molt alt de dades?
* Hi ha un esquema estable (ben estructurat)?
* Quins requisits qualitatius tenim: disponibilitat, escalabilitat, latència, rendiment, consistència...?

Si la resposta està a prop d'una aplicació monousuari, sense connexió amb altres clients, i poques dades, segurament podem gestionar-ho mitjançant **persistència en fitxer**. Caldria, en tot cas, decidir quin és el format d'aquest fitxer, ja que podem utilitzar solucions existents sense necessitar inventar-nos un format a mida. En POO, utilitzem el concepte de **serialització d'objectes**: generem una representació del graf d'objectes que permet restaurar-los quan l'aplicació torna a executar-se. El format podria ser a mida, utilitzant JSON, un arxiu de preferències clau-valor, etc.

Si la resposta s'assembla a aplicació multiusuari amb informació compartida per la xarxa i grans volums de dades, estem a prop de necessitar un **sistema de gestió de base de dades** (SGBD). En aquest cas, parlem de **mapatge d'objectes relacional (ORM)**. Aquest procés consisteix a interposar una capa entre la lògica i la persistència de l'aplicació, de tal forma que podem persistir utilitzant el paradigma d'orientació a objecte en lloc del llenguatge SQL. És un procés complex i [no exempte de problemes](https://en.wikipedia.org/wiki/Object-relational\_impedance\_mismatch). A Java es pot implementar a mida (JDBC) o bé utilitzar llibreries de mapatge ([JPA](https://en.wikipedia.org/wiki/Jakarta\_Persistence)).

Els SGBD resolen **problemes habituals** que ens trobem en el desenvolupament d'aplicacions. Entre ells:

* Definició, creació, manteniment i control d'accés a una base de dades.
* Gestió de transaccions i concurrència (segons el model).
* Facilitats per recuperar dades en cas de danys.
* Gestió d'autoritzacions i accés remot.
* Regles de comportament de les dades en funció de la seva estructura.

## Base de dades d'aplicació o d'integració

Una base de dades **d’integració** és una base de dades que actua com a magatzem de dades de diverses aplicacions i, per tant, integra dades d'aquestes aplicacions.

Una base de dades **d'aplicació** es controla i accedeix des d'una sola aplicació. Per a compartir dades amb altres aplicacions, l'aplicació que controla la base de dades hauria de proporcionar serveis.

La recomanació general és la d'evitar bases de dades d'integració. En general, les bases de dades d’integració comporten problemes greus perquè la base de dades esdevé un punt d’acoblament entre les aplicacions que hi accedeixen. Generalment es tracta d'un acoblament profund que augmenta significativament el risc que suposa canviar aquestes aplicacions i dificulta la seva evolució.

## Model relacional vs NoSQL

Les bases de dades actuals responen, moltes d'elles, al **model relacional**. Aquest model ha triomfat segurament gràcies a l'establiment d'un estàndard per a la gestió de dades, l'**SQL**. Existeixen alguns altres models que tenen sentit per a certs nínxols, i que cal considerar: bases de dades en graf, multivalor o orientades a objecte. Però han anat perdent ressò en favor de les bases de dades **NoSQL**. El creixement d'aquestes es veu afavorit pel Big Data i les aplicacions en temps real. Són sistemes habitualment no estructurats ([**sense esquema**](https://martinfowler.com/articles/schemaless/)), i poden persistir al costat de solucions relacionals en models de [persistència poliglota](https://en.wikipedia.org/wiki/Polyglot\_persistence).

Sense sortir del model relacional, solem tenir **extensions sense esquema**. Per exemple, camps amb contingut JSON. O taules d'atributs que permeten fer JOINs addicionals. Aquestes extensions ens permeten tenir dades sense esquema dins d'un esquema, tot i que aquestes dades no són tan accessibles des de consultes SQL.

El que cal evitar és tenir esquemes implícits al codi d'accés. Només en pocs casos pot tenir sentit no tenir-ne un esquema:

* Camps a mida imposats per l'usuari
* Objectes sense un tipus uniforme (esdeveniments)
* Pot ser més fàcil fer migracions d'esquemes (implícits)

Punts a considerar a l'hora de decidir-se:

* És una BBDD amb o sense esquema (relacionals vs NoSQL)?
* Existeixen relacions, que utilitzarem per navegar aquesta informació?
* La velocitat és un aspecte crític? Les relacionals sacrifiquen la velocitat en favor de la normalització.
* És important tenir escalabilitat? Les NoSQL escalen millor horitzontalment.
* Les relacionals ofereixen les propietats ACID, mentre les NoSQL són BASE.

## Característiques ACID

En el context de bases de dades, [**ACID**](https://en.wikipedia.org/wiki/ACID) (acrònim anglès de _Atomicity, Consistency, Isolation, Durability_) són tot un seguit de propietats que ha de complir tot sistema de gestió de bases de dades per tal de garantir que les transaccions (operacions sobre les dades) siguin fiables.

Concretament, l'acrònim ACID significa:

* **A**tomicitat: Una transacció o bé finalitza correctament i confirma o bé no deixa cap rastre de la seva execució.
* **C**onsistència: La concurrència de transaccions no pot produir resultats anòmals.
* **Aï**llament (o **I**solament): Cada transacció del sistema s'ha d'executar com si fos l'única que s'executa en aquell moment en el sistema.
* **D**urabilitat: Si es confirma una transacció, el resultat d'aquesta ha de ser definitiu i no es pot perdre.

## Característiques BASE

Les característiques BASE estan associades a les BBDD NoSQL. Es basen en el teorema CAP (Consistency-Availability-Partition Tolerance), que afirma que és molt difícil tenir més de dues d'aquestes propietats alhora.

Són l'acrònim de:

* **B**asic **A**vailability: la base de dades funciona la majoria del temps.
* **S**oft-State: no cal tenir consistència a l'escriptura, ni les rèpliques han de ser consistents.
* **E**ventual consistency: la consistència es pot tenir més tard en el temps (funcionament mandrós).
