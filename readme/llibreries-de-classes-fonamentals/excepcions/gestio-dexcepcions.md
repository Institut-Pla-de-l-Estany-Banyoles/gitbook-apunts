# Gestió d'excepcions

## Throws

Es pot tractar una excepció simplement fent throws:

```
public void metode() throws FileNotFoundException { ...
```

## Try-catch

Podem gestionar l'excepció rellançant-la:

```java
try {
catch (SomeException e} {
    throw new AnotherException("un missatge");
}
```

O bé fent accions per recuperar-nos:

```java
try {
catch (SomeException e} {
    return VALOR_PER_DEFECTE;
}
```

## Finally

Quan volem executar algun codi, passi o no passi l'excepció. Pot servir per alliberar recursos.

```java
try {
    // ...
} catch (SomeException e) {
    // ...
} finally {
    // el codi aqui sempre s'executarà 
}
```

## Try-with-resources

Permet treballar amb recursos, i tancar-los sense fer-ho explícitament al codi. Cal que el recurs implementi AutoCloseable.

```java
try (AutoCloseableObject o = new AutoCloseableObject()) {
  // ...
} catch (SomeException e) {
  // ...
}
```

## Multiples catch

Permet gestionar diverses excepcions. L'ordre és important: si tenim excepcions que comparteixen tipus, cal que estiguin les més específiques abans.

```java
try {
    // ...
} catch (SomeEspecificException e) {
    // ...
} catch (LessEspecificException e) {
    // ...
} catch (AnotherException e) {
    // ...
}
```

## Union

Permet gestionar diverses excepcions al mateix bloc.

```java
try {
    // ...
} catch (SomeException | SomeOtherException | AnotherException e) {
    // ...
}
```
