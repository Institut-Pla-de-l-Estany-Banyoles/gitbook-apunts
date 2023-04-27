# Indicacions

La tentació d'un programador podria ser utilitzar excepcions **unchecked**, ja que no cal gestionar-les ni declarar-les als mètodes.

Quan un mètode especifica una excepció a la seva signatura, està demanant a qui el crida què vol fer: si tornar a llençar o bé gestionar l'excepció. Les excepcions unchecked són el resultat d'esdeveniments no recuperables, i no té sentit que hagin de ser declarades (tot i que seria possible) per tot arreu, ja que el codi no seria clar.

**La regla seria**: si una crida pot recuperar-se d'una excepció, fes que sigui **checked**. Si no pot fer res, fes que sigui **unchecked**.

Alguns **anti-patrons** típics:

* Empassar-se excepcions
* Fer return a un finally
* Fer throw a un finally
* Utilitzar throw com a goto
