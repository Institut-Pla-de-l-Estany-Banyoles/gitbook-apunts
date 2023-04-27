# Llençant excepcions

## Checked

Es pot llençar, i cal especificar-ho.

```java
public void metode() throws SomeException {
    // ...
    throw new SomeException("some text");
}
```

## Unchecked

No cal especificar-la:

```java
public void metode() {
    // ...
    throw new SomeException("some text");
}
```

## Rethrowing

Tornem a llençar l'excepció gestionada:

```java
try {
    // ...
} catch (SomeException e) {
    throw e;
}
```

## Wrapping

Fem un embolcall:

```java
try {
    // ...
} catch (SomeException e) {
    throw new SomeOtherException("una explicació", e);
}
```

## Herència

Quan sobreescribim un mètode, podem fer que la subclasse tingui una signatura menys arriscada, o sigui, sense el throws.

Veure la [interpretació de les excepcions](https://jgregor5.gitlab.io/pindoles\_java/#interpretaci%C3%B3-de-les-excepcions).
