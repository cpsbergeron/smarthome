# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 10

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.

## Étape 1

Ajoute le bloc ``||LED:activer LED||`` dans le bloc ``||basic:au démarrage||``.

Supprime le bloc ``||basic:toujours||``.

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

Ajoute le bloc ``||music: régler le volume||``  sous le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran).

Remplace la valeur ``||music: 127 ||`` par la valeur ``||music: 100 ||``.

Le volume du haut-parleur du bouclier d'extension varie entre 0 et 255.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
music.setVolume(100)

```

## Étape 4

Ajoute le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse) de l'onglet ``||neopixel:  neopixel ||`` sous le bloc ``||music: régler le volume||``.

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
music.setVolume(100)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)

```

## Étape 5

Ajoute le bloc ``||neopixel:  régler couleur||`` sous le bloc ``||variables:  définir strip ||``.

Remplace la valeur ``||neopixel:  rouge ||`` par la valeur ``||neopixel: noir ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
music.setVolume(100)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))

```

## Étape 6

Ajoute le bloc ``||loops: chaque 500 ms||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

loops.everyInterval(500, function () {
	
})

```

## Étape 7

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||loops: chaque 500 ms||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
})

```

## Étape 8

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par la valeur ``||smarthome:P2||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 9

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Lumen ||`` sous le bloc ``||variables: définir Celsius ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau d'intensité lumineuse).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
})

```

## Étape 10

Modifie le bloc ``||smarthome:value of light intensity||`` (trad. : la valeur du niveau d'intensité lumineuse).

Remplace la valeur ``||smarthome:P1||`` par la valeur ``||smarthome:P3||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## Étape 11

Modifie le bloc ``||loops:chaque 500 ms||``.

Remplace la valeur ``||loops: 500 ||`` par le bloc ``||math:0 x 0||``.

Remplace la valeur ``||math:0||`` de gauche par la valeur ``||math:1000||``.

Remplace la valeur ``||math:0||`` de droite par la valeur ``||math:5||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(1000 * 5, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## Étape 12

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

## Étape 13

Remplace la valeur ``||OLED: " " ||`` du bloc ``||OLED: show string ||`` (trad. : montrer la ligne) par le mot ``||OLED: Celsius ||``.

Remplace la valeur ``||OLED: 0 ||`` du bloc ``||OLED: show number ||`` (trad. : montrer nombre) par le bloc ``||variables: Celsius ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Celsius = 0
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
})

```

## Étape 14

Ajoute le bloc ``||logic: si vrai alors ||`` sous le bloc ``||OLED: show number ||`` (trad. : montrer nombre).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Celsius = 0
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    if (true) {
    	
    }
})


```

## Étape 15

Modifie le bloc ``||logic: si vrai alors ||``.

Remplace la valeur ``||logic: vrai ||`` par le bloc ``||logic: 0 < 0 ||``.

Remplace la valeur ``||logic: 0 < 0 ||`` de gauche par le bloc ``||variables: Celsius ||``.

Remplace la valeur ``||logic: 0 < 0 ||`` de droite par la valeur ``||logic: 25 ||``

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Celsius = 0
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    if (Celsius < 25) {
    	
    }
})

```

## Étape 16

Ajoute le bloc ``||music: jouer tonalité ||`` dans le bloc ``||logic: si vrai alors ||``.

Remplace la valeur ``||music: Middle C ||`` par la valeur ``||music: Low C ||``.

Les autres valeurs du bloc ``||music: jouer tonalité ||`` demeurent les mêmes.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    let Celsius = 0
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    if (Celsius < 25) {
        music.play(music.tonePlayable(131, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})

```

## Étape 17

Ajoute le bloc ``||OLED: clear display ||`` (trad. : effacer l'écran) dans le bloc ``||input: lorsque le bouton B est pressé ||``.

Ajoute le bloc ``||OLED: draw loading bar ||`` (trad. : dessiner une barre de progression) sous le bloc ``||OLED: clear display ||``.

Remplace la valeur ``||OLED: 0 ||`` du bloc ``||OLED: draw loading bar ||`` (trad. : dessiner une barre de progression) par le bloc ``||variables: Lumen ||``.


```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.B, function () {
    let Lumen = 0
    OLED.clear()
    OLED.drawLoading(Lumen)
})

```

## Étape 18

Ajoute le bloc ``||logic: si vrai alors ||`` sous le bloc ``||OLED: draw loading bar ||`` (trad. : dessiner une barre de progression).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.B, function () {
    let Lumen = 0
    OLED.clear()
    OLED.drawLoading(Lumen)
    if (true) {
    	
    }
})

```

## Étape 19

Modifie le bloc ``||logic: si vrai alors ||``.

Remplace la valeur ``||logic: vrai ||`` par le bloc ``||logic: 0 > 0 ||``.

Remplace la valeur ``||logic: 0 > 0 ||`` de gauche par le bloc ``||variables: Lumen ||``.

Remplace la valeur ``||logic: 0 > 0 ||`` de droite par la valeur ``||logic: 40 ||``

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.B, function () {
    let Lumen = 0
    OLED.clear()
    OLED.drawLoading(Lumen)
    if (Lumen > 40) {
    	
    }
})


```

## Étape 20

Ajoute le bloc ``||music: jouer tonalité ||`` dans le bloc ``||logic: si vrai alors ||``.

Remplace la valeur ``||music: Middle C ||`` par la valeur ``||music: High B ||``.

Les autres valeurs du bloc ``||music: jouer tonalité ||`` demeurent les mêmes.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.B, function () {
    let Lumen = 0
    OLED.clear()
    OLED.drawLoading(Lumen)
    if (Lumen > 40) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})

```

## Étape 21

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    OLED.clear()
    OLED.writeStringNewLine("Celsius")
    OLED.writeNumNewLine(Celsius)
    if (Celsius < 25) {
        music.play(music.tonePlayable(131, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
input.onButtonPressed(Button.B, function () {
    OLED.clear()
    OLED.drawLoading(Lumen)
    if (Lumen > 40) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
music.setVolume(100)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
loops.everyInterval(1000 * 5, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.