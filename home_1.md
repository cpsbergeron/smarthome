# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 1

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.

## Étape 1

Ajoute le bloc ``||LED:activer LED||`` dans le bloc ``||basic:au démarrage||``.

La valeur ``||logic:faux||`` du bloc ``||LED:activer LED||`` demeure la même.

Certaines broches (ex. :  P3, P4, P6, etc.) sont utilisées par le micro:bit pour allumer les lumières LEDs.

Cette séquence de programmation permet de désactiver les lumières LEDs du micro:bit pour les utiliser avec le bouclier d'extension.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
basic.forever(function () {
	
})

```

## Étape 2

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

Les valeurs ``||OLED: 128 ||`` et ``||OLED: 64 ||`` sont les dimensions (en pixels) de l'écran.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
	
})

```

## Étape 3

Ajoute le bloc ``||OLED: clear OLED ||`` (trad. : effacer l'écran) dans le bloc ``||basic:toujours||``.

Ajoute le bloc ``||OLED: show string ||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("")
})

```

## Étape 4

Remplace la valeur ``||OLED: " " ||`` du bloc ``||OLED: show string ||`` (trad. : montrer la ligne) par ton prénom (sans accent).

Exemple : Marc-Andre au lieu de Marc-André.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Marc-Andre")
})

```

## Étape 5

Ajoute le bloc ``||basic: pause (ms)||`` sous le bloc ``||OLED: show string ||``.

Remplace la valeur  ``||basic: 100||`` du bloc ``||basic: pause (ms)||`` par ``||basic: 5000||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Marc-Andre")
    basic.pause(5000)
})

```

## Étape 6

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    OLED.clear()
    OLED.writeStringNewLine("Marc-Andre")
    basic.pause(5000)
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.