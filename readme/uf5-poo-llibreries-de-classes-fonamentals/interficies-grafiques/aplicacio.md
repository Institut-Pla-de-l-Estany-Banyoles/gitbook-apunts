# Aplicació

Ara veure'm un exemple mínim d'aplicació. Tenim els següents components gràfics:

* Stage: la finestra principal
* Scene: el contenidor del graf d'elements gràfics
* Graf scene: la jerarquia d'elements gràfics, en aquest exemple: Label.

```java
public class JavaWorldApp extends Application {  
    @Override     
    public void start(Stage primaryStage) throws Exception { 
        // creació del stage, scene i scene graph
        primaryStage.setTitle("Hello world App");
        Label label = new Label("Hello World!");
        Scene scene = new Scene(label, 400, 200);
        primaryStage.setScene(scene);
        primaryStage.show();
    }         
    public static void main(String args[]){           
        launch(args);      
    } 
}
```
