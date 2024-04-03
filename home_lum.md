# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 3

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.

## Étape 1

Ajoute le bloc ``||LED:activer LED||`` dans le bloc ``||basic:au démarrage||``.

La valeur ``||logic:faux||`` du bloc ``||LED:activer LED||`` demeure la même.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
basic.forever(function () {
	
})

```

## Étape 2

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``.

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

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

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:LED||``.

Ajoute le bloc ``||variables: définir LED ||`` dans le bloc ``||basic: toujours ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||input:niveau d'intensité lumineuse||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let LED = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    LED = input.lightLevel()
})



```

## Étape 5

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) sous le bloc ``||variables: définir LED ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let LED = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    LED = input.lightLevel()
    OLED.clear()
})

```

## Étape 6

Ajoute le bloc ``||OLED:show number||`` (trad. : montrer le nombre) sous le bloc ``||OLED: clear OLED display ||`` (trad. : effacer l'écran).

Remplace la valeur ``||OLED:0||`` par le bloc ``||variables: LED ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let LED = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    LED = input.lightLevel()
    OLED.clear()
    OLED.writeNumNewLine(LED)
})

```

## Étape 7

Ajoute le bloc ``||basic:pause (ms)||`` sous le bloc ``||OLED: show number ||`` (trad. : montrer nombre).

Remplace la valeur ``||basic:100||`` par le bloc ``||basic:3000||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let LED = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    LED = input.lightLevel()
    OLED.clear()
    OLED.writeNumNewLine(LED)
    basic.pause(3000)
})



```

## Étape 8

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let LED = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    LED = input.lightLevel()
    OLED.clear()
    OLED.writeNumNewLine(LED)
    basic.pause(3000)
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.