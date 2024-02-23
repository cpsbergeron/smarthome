# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 8

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

Ajoute le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse) de l'onglet ``||neopixel:  neopixel ||`` sous le bloc ``||OLED: initialize OLED ||``.

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

```

## Étape 4

Crée une ``||variables: variable||`` et donne lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||basic: toujours ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
})

```

## Étape 5

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P2||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})


```

## Étape 6

Crée une ``||variables: variable||`` et donne lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Lumen ||`` sous le bloc ``||variables: définir Celsius ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau d'intensité lumineuse).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
})


```

## Étape 7

Modifie le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau d'intensité lumineuse).

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P3||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})


```

## Étape 8

Ajoute le bloc ``||logic:si vrai alors sinon||`` sous le bloc ``||variables: définir Lumen ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (true) {
    	
    } else {
    	
    }
})

```

## Étape 9

Modifie le bloc ``||logic:si vrai alors sinon||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic: et||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (true && true) {
    	
    } else {
    	
    }
})


```

## Étape 10

Modifie le bloc ``||logic: et||``.

Remplace l'espace de gauche par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:25||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && true) {
    	
    } else {
    	
    }
})


```

## Étape 11

Modifie le bloc ``||logic: et||``.

Remplace l'espace de droite par le bloc ``||logic:0 < 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Lumen||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:40||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
    	
    } else {
    	
    }
})

```


## Étape 12

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:  si ||``.

Remplace la valeur ``||neopixel:  rouge ||`` par la valeur ``||neopixel:  noir ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
    } else {
    	
    }
})

```

## Étape 13

Ajoute le bloc ``||music:  jouer tonalité||`` sous le bloc ``||neopixel:  régler couleur||``.

Les valeurs ``||music:  Middle C||``, ``||music:  1 temps||`` et ``||music:  jusqu'à la fin||`` demeurent les mêmes.


```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
    	
    }
})


```

## Étape 14

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:  sinon ||``.

Remplace la valeur ``||neopixel:  rouge ||`` par la valeur ``||neopixel:  blanc ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.White))
    }
})


```

## Étape 15

Ajoute le bloc ``||OLED: clear OLED ||`` (trad. : effacer l'écran) dans le bloc ``||input:lorsque le bouton A est pressé||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
})
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.White))
    }
})


```

## Étape 16

Ajoute le bloc ``||OLED: show string ||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED ||`` (trad. : effacer écran).

Remplace la valeur ``||OLED: " " ||`` par le mot ``||OLED:Celsius||``. 

Ajoute le bloc ``||OLED: show number ||`` (trad. : montrer le nombre) sous le bloc ``||OLED: show string ||``.

Remplace la valeur ``||OLED: 0 ||`` par le bloc ``||variables:Celsius||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks
input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
})
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.White))
    }
})


```

## Étape 17

Ajoute le bloc ``||OLED: show string ||`` (trad. : montrer la ligne) sous le bloc ``||OLED: show number ||`` (trad. : montrer le nombre).

Remplace la valeur ``||OLED: " " ||`` par le mot ``||OLED:Lumen||``. 

Ajoute le bloc ``||OLED: show number ||`` (trad. : montrer le nombre) sous le bloc ``||OLED: show string ||``.

Remplace la valeur ``||OLED: 0 ||`` par le bloc ``||variables:Lumen||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    OLED.writeStringNewLine("Lumen")
    OLED.writeNumNewLine(Lumen)
})
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.White))
    }
})


```

## Étape 17

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    OLED.writeStringNewLine("Lumen")
    OLED.writeNumNewLine(Lumen)
})
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    if (Celsius > 25 && Lumen < 40) {
        strip.showColor(neopixel.colors(NeoPixelColors.Black))
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    } else {
        strip.showColor(neopixel.colors(NeoPixelColors.White))
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.