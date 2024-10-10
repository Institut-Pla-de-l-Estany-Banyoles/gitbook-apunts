# Conversions de tipus

De la mateixa manera que el fet de treballar amb dades implica que hi ha d'haver uns operadors per manipular-les, també es genera la necessitat de tenir els mecanismes necessaris per poder convertir-les d'uns tipus a altres.

### **Conversió implícita o winderning**

Es produeixen de manera automàtica quan Java transforma un tipus de dades més petit a un tipus més gran. Aquest tipus de conversió és segur perquè no hi ha pèrdua de precisió o informació en el procés.

#### Tipus de conversions implícites:

* De `byte` a `short`, `int`, `long`, `float` o `double`
* De `short` a `int`, `long`, `float` o `double`
* De `int` a `long`, `float` o `double`
* De `long` a `float` o `double`
* De `float` a `double`

#### Exemple

```java
int numEnter = 10;
double numDecimal = numEnter;  // Conversió implícita de int a double => 10.0
```

En aquest exemple, la variable `numEnter` de tipus `int` es converteix automàticament a un valor de tipus `double` perquè `double` és un tipus més gran i pot contenir valors enters sense pèrdua d'informació.

#### Més exemples de conversions implícites:

```java
byte b = 100;
int i = b;     // Conversió implícita de byte a int

float f = i;   // Conversió implícita de int a float

double d = f;  // Conversió implícita de float a double
```

### **Conversió explícita, casting o narrowing**

Es fa intencionadament pel programador. Són necessàries quan es vol convertir un tipus de dades més gran en un de més petit. Aquest tipus de conversió pot implicar una pèrdua de precisió o informació, per la qual cosa Java requereix que la conversió sigui explícita per part del programador.

#### Tipus de conversions explícites:

* De `double` a `float`, `long`, `int`, `short` o `byte`
* De `float` a `long`, `int`, `short` o `byte`
* De `long` a `int`, `short` o `byte`
* De `int` a `short` o `byte`

#### Exemple

```java
double numDecimal = 9.78;
int numEnter = (int) numDecimal;  // Conversió explícita de double a int => 9
```

En aquest exemple, la variable `numDecimal` de tipus `double` es converteix explícitament a un `int`. Això implica una pèrdua de precisió, ja que el valor decimal es redueix a la seva part entera.

#### Més exemples de conversions explícites:

```java
double d = 5.99;
int i = (int) d;   // Conversió explícita de double a int

long l = 1000L;
short s = (short) l;  // Conversió explícita de long a short

float f = 3.14f;
byte b = (byte) f;  // Conversió explícita de float a byte
```
