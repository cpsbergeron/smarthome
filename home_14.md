# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 14

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

```

## Étape 2

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``.

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

Les valeurs ``||OLED: 128 ||`` et ``||OLED: 64 ||`` sont les dimensions (en pixels) de l'écran.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)

```

## Étape 3


Ajoute le bloc ``|| pins: régler position servo ||``  sous le bloc  ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran).

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins: 0 ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
pins.servoWritePin(AnalogPin.P8, 0)

```

## Étape 4

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Lumen ||`` dans le bloc ``||basic: toujours ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau de l'intensité lumineuse).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
})

```

## Étape 5

Modifie le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau de l'intensité lumineuse)..


Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P3||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})


```

## Étape 6

Ajoute le bloc ``||logic:si vrai alors sinon||`` sous le bloc ``||variables: définir Lumen ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (true) {
    	
    } else {
    	
    }
})

```

## Étape 7

Modifie le bloc ``||logic:si vrai alors sinon||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Lumen||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:50||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen > 50) {
    	
    } else {
    	
    }
})


```

## Étape 8

Ajoute le bloc ``|| pins: régler position servo ||``  dans le bloc  ``|| logic: si alors ||``.

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

La valeur ``|| pins: 180 ||`` du bloc ``|| pins: régler position servo ||`` demeure la même.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen > 50) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
    	
    }
})

```

## Étape 9

Ajoute le bloc ``|| pins: écrire sur la broche ||``  dans le bloc  ``|| logic: sinon ||``.

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 0 ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen > 50) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})


```

## Étape 10

Ajoute le bloc ``||OLED: clear display ||`` (trad. : effacer l'écran) dans le bloc ``||input: lorsque le bouton A est pressé ||``.

Ajoute le bloc ``||OLED: show string ||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear display ||``.

Ajoute le bloc ``||OLED: show number ||`` (trad. : montrer le nombre) sous le bloc ``||OLED: show string ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("")
    OLED.writeNumNewLine(0)
})

```

## Étape 11

Remplace la valeur ``||OLED: " " ||`` du bloc ``||OLED: show string ||`` (trad. : montrer la ligne) par le mot ``||OLED: Lumen ||``.

Remplace la valeur ``||OLED: 0 ||`` du bloc ``||OLED: show number ||`` (trad. : montrer nombre) par le bloc ``||variables: Lumen ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Lumen = 0
    OLED.clear()
    OLED.writeStringNewLine("Lumen")
    OLED.writeNumNewLine(Lumen)
})

```

## Étape 12

Voici la programmation complète du programme.


```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("Lumen")
    OLED.writeNumNewLine(Lumen)
})
let Lumen = 0
led.enable(false)
OLED.init(128, 64)
pins.servoWritePin(AnalogPin.P8, 0)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen > 50) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.