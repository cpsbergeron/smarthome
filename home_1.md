# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 1

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.

## Étape 1

Ajoute le bloc ``||LED:activer LED||`` dans le bloc ``||basic:au démarrage||``.

La valeur ``||logic:faux||`` du bloc ``||LED:activer LED||`` demeure la même.

Certaines broches (ex. :  P3, P4, P6, etc.) sont utilisées par le micro:bit pour allumer les lumières LEDs.

Cette séquence de programmation permet de désactiver les lumières LEDs du micro:bit pour les utiliser avec le bouclier d'extension.

```blocks

led.enable(false)
basic.forever(function () {
	
})

```

## Étape 2

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

Les valeurs ``||OLED: 128 ||`` et ``||OLED: 64 ||`` sont les dimensions (en pixels) de l'écran.

```blocks

led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
})

```

## Étape 3

Ajoute le bloc ``||OLED: clear OLED ||`` (trad. : effacer l'écran) dans le bloc ``||basic:toujours||``.

Ajoute le bloc ``||OLED: show string ||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED ||``.


```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("")
})

```

## Étape 4

Ajoute le bloc ``||text: concétanation ||`` dans le bloc ``||OLED: show string ||`` (trad. : montrer la ligne).

Appuie sur le ``||text: + ||`` du bloc ``||text: concétanation ||`` pour ajouter un espace supplémentaire.


```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Bonjour" + "Monde" + "")
})

```

## Étape 5

Remplace les valeurs du bloc ``||text: concétanation ||``.

Remplace le premier espace par ton ``||text: prénom ||``.

Laisse le deuxième espace vide.

Remplace le troisième espace par ton nom de ``||text: nom de famille ||``.

** Exemple : Sebastien au lieu de Sébastien. **


```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Sebastien" + "" + "Bergeron")
})

```

## Étape 6

Ajoute le bloc ``||basic: pause (ms)||`` sous le bloc ``||OLED: show string ||``.

Remplace la valeur  ``||basic: 100||`` du bloc ``||basic: pause (ms)||`` par ``||basic: 2000||``.

```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Sebastien" + "" + "Bergeron")
    basic.pause(2000)
})

```

## Étape 7

Voici la programmation complète du programme.

```blocks

OLED.init(128, 64)
led.enable(false)
basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Sebastien" + "" + "Bergeron")
    basic.pause(2000)
})


```

```package

tinkertanker/pxt-smarthome

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.