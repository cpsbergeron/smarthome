# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 13

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

Ajoute le bloc ``|| pins: écrire sur la broche ||``  sous le bloc  ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran).

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

La valeur ``|| pins: 0 ||`` du bloc ``|| pins: écrire sur la broche ||`` demeure la même.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

led.enable(false)
OLED.init(128, 64)
pins.digitalWritePin(DigitalPin.P12, 0)

```

## Étape 4

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||basic: toujours ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P0)
})

```

## Étape 5

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P0||`` par ``||smarthome:P2||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 6

Ajoute le bloc ``||logic:si vrai alors sinon||`` sous le bloc ``||variables: définir Celsius ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```


```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    if (true) {
        
    } else {
        
    }
})

```

## Étape 7

Modifie le bloc ``||logic:si vrai alors sinon||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:25||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    if (Celsius > 25) {
        
    } else {
        
    }
})

```

## Étape 8

Ajoute le bloc ``|| pins: écrire sur la broche ||``  dans le bloc  ``|| logic: si alors ||``.

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

Remplace la valeur ``|| pins: 0 ||`` par ``|| pins : 1 ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    if (Celsius > 25) {
        pins.digitalWritePin(DigitalPin.P12, 1)
    } else {
        
    }
})

```

## Étape 9

Ajoute le bloc ``|| pins: écrire sur la broche ||``  dans le bloc  ``|| logic: sinon ||``.

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

Remplace la valeur ``|| pins: 0 ||`` par ``|| pins : 0 ||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    if (Celsius > 25) {
        pins.digitalWritePin(DigitalPin.P12, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P12, 0)
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

## Étape 12

Voici la programmation complète du programme.

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
let Celsius = 0
led.enable(false)
OLED.init(128, 64)
pins.digitalWritePin(DigitalPin.P12, 0)
basic.forever(function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    if (Celsius < 25) {
        pins.digitalWritePin(DigitalPin.P12, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P12, 0)
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.