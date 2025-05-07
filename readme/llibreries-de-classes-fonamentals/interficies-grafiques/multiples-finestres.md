# Múltiples finestres

Una stage equival a una finestra.

Podem canviar el contingut d'una finestra modificant el graf de scenes. Això es pot fer amb el mètode:

* `scene.setRoot(Parent node)`

Podem crear finestres modals de tres tipus:

* Alert
* TextInputDialog
* ChoiceDialog

El mètode start(Stage primaryStage) d'una aplicació permet establir la finestra principal, però es podrien crear noves, modals o no. Per fer-ho, crear una stage, i utilitzar els mètodes:

* `stage.initOwner(Window w)`
* `stage.initModality(Modality m)`

Modality pot tenir tres valors:

* `Modality.NONE`: un stage que no bloqueja cap altra finestra.
* `Modality.WINDOW_MODAL`: un stage que impedeix que els esdeveniments d’entrada es lliurin a totes les finestres des del seu pare fins a l’arrel. La seva arrel és la finestra més avantpassada sense owner.
* `Modality.APPLICATION_MODAL`: un stage que impedeix que els esdeveniments d'entrada es lliurin a totes les finestres des de la mateixa aplicació, excepte els de la seva jerarquia de fills.
