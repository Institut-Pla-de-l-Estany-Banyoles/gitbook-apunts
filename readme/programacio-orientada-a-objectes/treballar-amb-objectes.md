# Treballar amb objectes

A l'apartat anterior, hem vist com definir les Classes, aquestes plantilles que ens defineixen les característiques i capacitats de les entitats, i ens permeten la creació d'aquestes.

### Crear Objectes

La **creació d'objectes** a partir d'una classe, l'anomenem **instanciar**. Quan nosaltres creem nous objectes (`new`), el que estem fent és instanciar objectes de la classe. Crear noves còpies de la plantilla definida per la classe.

Per crear instàncies de la classe, utilitzem els seus **`constructors`.** Segons els constructors que tingui definida la classe, podrem inicialitzar els valors que tindrà l'objecte o només reservar el seu espai a memòria i obtenir-ne la referència.

```java
Alumne unAlumne = new Alumne();
```

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt="" width="563"><figcaption></figcaption></figure>

```java
Alumne unAlumne = new Alumne("Joan", 25, 7.5f);
```

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt="" width="563"><figcaption><p>Imatges de Fernando Porrino</p></figcaption></figure>

En el cas del constructor amb paràmetres anteriors, podem veure que a part de crear l'objecte i reservar l'espai a memòria, ens ha assignat els valors inicials de l'objecte amb "Joan" al camp `nom`, 25 a la seva `edat` i 7.5 a la seva `nota`.

***

### Accedir a les propietats dels objectes

Per accedir a les propietats d'un mètode usarem els mètodes de consulta i modificació (`getters i setters`). En cas que l'objecte tingui algun **atribut públic**, podrem accedir directament a aquesta propietat.

{% hint style="warning" %}
Els atributs públics s'han de fer en **situacions molt concretes que el disseny de la classe ho requereixi.** En cas de definir-ne, **s'ha de garantir que la seva modificació o consulta no posi en risc la integritat de l'objecte o classe.**
{% endhint %}

#### Consulta

```java
String nomAlumne = unAlumne.getNom();
int edatAlumne = unAlumne.getEdat();

if (unAlumne.isAprovat()){
    System.out.println("Felicitats, bona feina!");
}else{
    System.out.println("Aquest cop no ha anat bé, ànims per la pròxima!");
}


//En el cas d'atributs públics, podem accedir directament a la seva propietat
String elDNI = unAlumne.DNI;

//En comptes d'haver de fer
String elDNI = unAlumen.getDNI();
```

#### Modificació

Per accedir a les propietats d'un mètode usarem els mètodes de consulta i modificació (`getters i setters`). En cas que l'objecte tingui algun **atribut públic**, podrem accedir directament a aquesta propietat.

```java
unAlumne.setNom("Marc");
unAlumne.setEdat(30);

if (nota >= 5){
    unAlumne.setAprovat(true);
}else{
    unAlumne.setAprovat(false);
}
```

***

### Invocar els mètodes

Per executar les accions associades als objectes o les classes, hem d'utilitzar els seus mètodes. Igual que a l'apartat anterior, aquí ho fem amb l'operador `.` després del nom l'objecte.

```java
unAlumne.realitzarExamen("/programació/examens/prova1.pdf");

unaPersona.saluda();

jugador.ataca(enemic);
```
