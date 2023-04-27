# Excepcions pròpies

Habitualment, tenim diverses signatures per crear un objecte d'excepció. Tot i que els paràmetres són lliures (podem afegir els que ens ajudin a interpretar el nostre error particular), dos sovintegen:

* el missatge d'error, un String.
* una excepció, la causa. Permet enllaçar excepcions amb les seves causes (**wrapping**).

Per exemple, una excepció checked estenent `Exception`:

```java
public class SomeException extends Exception {    
    public SomeException (String message, Throwable t) {
        super(message, t);
    }
}
```

Per exemple, una excepció unchecked estenent `RuntimeException`:

```java
public class SomeException extends RuntimeException {
    public SomeException (String message, Throwable t) {
        super(message, t);
    }
}
```
