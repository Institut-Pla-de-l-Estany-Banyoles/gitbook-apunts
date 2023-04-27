# Tipus de nodes

Els nodes poden ser de tres tipus:

1. Arrel: el primer del graf. Pot ser del tipus 2.
2. Parent (Branch)
   * **Group**: és un node col.lectiu que renderitza tots els seus fills en ordre.
   * **Region**: base per als [controls UI](https://docs.oracle.com/javafx/2/ui\_controls/jfxpub-ui\_controls.htm), com Chart, Pane i Control.
   * **WebView**: gestiona l'engine web.
3. Leaf: no conté nodes fill.

Els nodes (components visuals) inclouen:

* Figures geomètriques (`javafx.scene.shape`): Circle, Rectangle, Polygon, etc.
* Controls (`javafx.scene.control`): Button, Checkbox, Choice Box, Text Area, etc.
* Contenidors (`javafx.scene.layout`): Border Pane, Grid Pane, Flow Pane, etc.
* Elements media (Audio, Video, Image)

Cada tipus de node té mètodes que permeten modificar el seu aspecte o el seu contingut, habitualment són getters i setters.

Per exemple: un Label és un node amb un text, i té dos mètodes per accedir i canviar el contingut: `setText i getText`.

També hi ha la possibilitat de treballar directament amb un canvas, dibuixant en ell. És la classe [Canvas](https://openjfx.io/javadoc/11/javafx.graphics/javafx/scene/canvas/Canvas.html). [Aquí hi ha una explicació de com funciona](https://docs.oracle.com/javafx/2/canvas/jfxpub-canvas.htm).
