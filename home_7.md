# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 7

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

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``.

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

Ajoute le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse) de l'onglet ``||neopixel:  neopixel ||`` sous le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran).

Modifie le bloc ``||variables:  définir strip ||``.

Remplace la valeur ``||neopixel:  P0 ||`` par ``||neopixel:  P1 ||``.

Remplace la valeur ``||neopixel:  24 ||`` par  ``||neopixel:  1 ||``.

La valeur ``||neopixel:  RGB ||`` demeure la même.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
	
})

```

## Étape 4

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Lumen ||`` dans le bloc ``||basic: toujours ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of light intensity||`` (trad. : le niveau d'intensité lumineuse).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks
let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
})

```

## Étape 5

Modifie le bloc ``||smarthome:value of light intensity||`` (trad. : le niveau d'intensité lumineuse).

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P3||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
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
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (true) {
    	
    } else {
    	
    }
})

```

## Étape 7

Modifie le bloc ``||logic:si vrai alors sinon||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 < 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Lumen||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:40||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen < 40) {
    	
    } else {
    	
    }
})

```

## Étape 8

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:si||``.

La valeur ``||neopixel: rouge ||`` demeure la même.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Red))
    } else {
    	
    }
})

```

## Étape 9

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:  sinon ||``.

Remplace la valeur ``||neopixel:  rouge ||`` par la valeur ``||neopixel:  noir ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Red))
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
    }
})

```

## Étape 10

Ajoute le bloc ``||OLED: clear OLED ||`` (trad. : effacer l'écran) dans le bloc ``||input:lorsque le bouton A est pressé||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
})

```

## Étape 11

Ajoute le bloc ``||OLED: show number ||`` (trad. : montrer le nombre) sous le bloc ``||OLED: clear OLED ||`` (trad. : effacer écran).

Remplace la valeur ``||OLED: 0 ||`` par le bloc ``||variables:Lumen||``.


```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Lumen = 0
    OLED.clear()
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
    OLED.writeNumNewLine(Lumen)
})
let Lumen = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Red))
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
    }
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.