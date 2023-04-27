# FXML

A l'hora de crear elements gràfics tenim dues opcions: crear-los programàticament o bé amb un arxiu de tipus XML anomenat FXML. El format FXML facilita el dibuix mitjançant eines de disseny com el [Scene Builder](https://www.oracle.com/java/technologies/javase/javafxscenebuilder-info.html). A més, permet associar el codi XML amb el codi Java:

* Cal definir un controlador, un objecte Java que serà el nexe de comunicació del món XML i el món Java. Aquest ha d'implementar la interfície javafx.fxml.Initializable.
* Defineix associacions entre objectes al FXML (propietat `fx:id` dels elements) i objectes Java del controlador.
* Defineix associacions entre accions al FXML (propietat `onAction` dels elements) i mètodes Java del controlador.

Per a carregar un arxiu FXML cal fer les següents operacions:

```java
FXMLLoader loader = new FXMLLoader();   
loader.setController(controlador);
loader.setLocation(getClass().getResource("/cami/arxiu.fxml"));
Parent parent = loader.load();
Scene scene = new Scene(parent);
```

El camí pot ser absolut (utilitzant la jerarquia de paquets) o bé relatiu al paquet actual, sense utilitzar camí.

Les associacions al FXML es poden fer utilitzant un ID i amb una action:

```xml
<Label fx:id="inputLabel"> ... </Label>
...
<Button ... onAction="#onButtonClick" ... />
```

Aquest codi es correspondrà amb el següent al controlador:

```java
@FXML
private Label inputLabel;
...
@FXML
private void onButtonClick(ActionEvent event) {
    ...
}
```

Amb aquest codi podem accedir a l'etiqueta definida al XML mitjançant l'objecte `inputLabel`, i cada cop que es cliqui al botó es cridarà al mètode `onButtonClick`.
