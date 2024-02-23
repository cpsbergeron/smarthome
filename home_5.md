# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 5

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

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||input:lorsque le bouton A est pressé ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
})

```

## Étape 4

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P2||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 5

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) sous le bloc ``||variables: définir Celsius ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
})

```

## Étape 6

Ajoute le bloc ``||OLED:show number||`` (trad. : montrer le nombre) sous le bloc ``||OLED: clear OLED display ||`` (trad. : effacer l'écran).

Remplace la valeur ``||OLED:0||`` par le bloc ``||variables: Celsius ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeNumNewLine(Celsius)
})

```
## Étape 7

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeNumNewLine(Celsius)
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.

## Étape 8

Certains blocs ont été ajoutés pour réaliser le défi. Ils sont placés dans le désordre.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeNumNewLine(Celsius)
})
input.onButtonPressed(Button.AB, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let strip: neopixel.Strip = null
let Lumen = 0
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
    basic.pause(100)
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.