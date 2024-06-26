# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 10

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

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

Les valeurs ``||OLED: 128 ||`` et ``||OLED: 64 ||`` sont les dimensions (en pixels) de l'écran.

```blocks

led.enable(false)
OLED.init(128, 64)

```

## Étape 3A

Ajoute le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse) de l'onglet ``||neopixel:  neopixel ||`` sous le bloc ``||OLED: initialize OLED ||``.

Remplace la valeur ``||neopixel:  P0 ||`` par ``||neopixel:  P1 ||``.

Remplace la valeur ``||neopixel:  24 ||`` par ``||neopixel:  1 ||``.

```blocks

OLED.init(128, 64)
led.enable(false)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)

```

## Étape 3B

Ajoute le bloc ``||music:  régler volume ||`` de l'onglet ``||music:  musique ||`` sous le bloc ``||variables:  définir strip ||``.

Remplace la valeur ``||music:  127 ||`` par ``||music:  255 ||``.

```blocks

OLED.init(128, 64)
led.enable(false)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
music.setVolume(255)

```

## Étape 4

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||loops: chaque 500 ms||``.

Ajoute le bloc ``||variables: définir Lumen ||`` sous le bloc ``||variables: définir Celsius ||``.

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(500, function () {
    Celsius = 0
    Lumen = 0
})

```

## Étape 5

Remplace la valeur ``||variables:0||`` du bloc ``||variables: définir Celsius ||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P2||``.

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = 0
})

```

## Étape 6

Remplace la valeur ``||variables:0||`` du bloc ``||variables: définir Lumen ||`` par le bloc ``||smarthome:value of light||`` (trad. : la valeur de la luminosité).

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P3||``.

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})


```

## Étape 7

Modifie le bloc ``||loops: chaque 500 ms||``.

Remplace la valeur ``||loops: 500||`` par ``||loops: 2500||``.

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(2500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## Étape 8

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) sous le bloc ``||variables: définir Lumen ||``.

```blocks

let Celsius = 0
let Lumen = 0
loops.everyInterval(2500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
})


```

## Étape 9

Ajoute deux blocs ``||OLED:show string||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED display ||`` (trad. : effacer l'écran).

Remplace les valeurs ``||OLED:" "||`` par les blocs ``||text: concaténation ||``.

```blocks

let Lumen = 0
let Celsius = 0
loops.everyInterval(2500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Bonjour" + "Monde")
    OLED.writeStringNewLine("Bonjour" + "Monde")
})

```

## Étape 10

Modifie le premier bloc ``||text: concaténation ||``.

Appuie sur le ``||text: + ||`` du bloc ``||text: concétanation ||`` pour ajouter un espace supplémentaire.

Remplace la valeur ``||text: Bonjour ||`` par ``||text: Celsius ||``.

Remplace la valeur ``||text: Monde ||`` par ``||text: : ||``.

Remplace la valeur ``||text: " " ||`` par le bloc ``||variables: Celcius||``.

```blocks

let Lumen = 0
let Celsius = 0
loops.everyInterval(2500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
    OLED.writeStringNewLine("Bonjour" + "Monde")
})

```

## Étape 11

Modifie le deuxième  bloc ``||text: concaténation ||``.

Appuie sur le ``||text: + ||`` du bloc ``||text: concétanation ||`` pour ajouter un espace supplémentaire.

Remplace la valeur ``||text: Bonjour ||`` par ``||text: Lumen ||``.

Remplace la valeur ``||text: Monde ||`` par ``||text: : ||``.

Remplace la valeur ``||text: " " ||`` par le bloc ``||variables: Lumen||``.

```blocks

let Lumen = 0
loops.everyInterval(2500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
    OLED.writeStringNewLine("Lumen" + ":" + Lumen)
})


```
## Étape 12

Ajoute le bloc ``||logic:si||`` dans le bloc ``||basic: toujours ||``.

```blocks

basic.forever(function () {
    if (true) {
    	
    }
})

```

## Étape 13

Modifie le bloc ``||logic:si ||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:25||``.


```blocks

basic.forever(function () {
    let Celsius = 0
    if (Celsius > 25) {
    	
    }
})

```

## Étape 14

Ajoute le bloc ``||music: jouer mélodie||`` dans le bloc ``||logic:si ||``.

Remplace la valeur ``||music: dadadum||`` par une mélodie de ton choix.

Remplace la valeur ``||music: en arrière-plan||`` par ``||music: jusqu'à la fin||``.

```blocks

let Celsius = 0
basic.forever(function () {
    if (Celsius > 25) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.InBackground)
    }
})

```
## Étape 15

Ajoute le bloc ``||logic:si||`` sous le bloc ``||logic: si ||``.

```blocks

let Celsius = 0
basic.forever(function () {
    if (Celsius > 25) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.UntilDone)
    }
    if (true) {
    	
    }
})

```

## Étape 16

Modifie le deuxième bloc ``||logic:si ||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 < 60||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Lumen||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:60||``.


```blocks

let Celsius = 0
let Lumen = 0
basic.forever(function () {
    if (Celsius > 25) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.UntilDone)
    }
    if (Lumen < 60) {
    	
    }
})

```

## Étape 17

Ajoute le bloc ``||music: jouer mélodie||`` dans le bloc ``||logic:si ||``.

Remplace la valeur ``||music: dadadum||`` par une mélodie de ton choix.

Remplace la valeur ``||music: en arrière-plan||`` par ``||music: jusqu'à la fin||``.

```blocks

let Celsius = 0
let Lumen = 0
basic.forever(function () {
    if (Celsius > 25) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.UntilDone)
    }
    if (Lumen < 60) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Entertainer), music.PlaybackMode.UntilDone)
    }
})

```

## Étape 18

Voici la programmation complète du tutoriel.

```blocks

let Lumen = 0
let Celsius = 0
OLED.init(128, 64)
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
music.setVolume(255)
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadLightIntensity(AnalogPin.P2)
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
    OLED.writeStringNewLine("Lumen" + ":" + Lumen)
})
basic.forever(function () {
    if (Celsius > 20) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.UntilDone)
    }
    if (Lumen < 60) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Entertainer), music.PlaybackMode.InBackground)
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.