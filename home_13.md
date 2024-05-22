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
basic.forever(function () {
	
})

```

## Étape 2

Ajoute le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran) sous le bloc ``||LED:activer LED||``.

Les valeurs du bloc ``||OLED: initialize OLED ||`` demeurent les mêmes.

Les valeurs ``||OLED: 128 ||`` et ``||OLED: 64 ||`` sont les dimensions (en pixels) de l'écran.

```blocks

led.enable(false)
OLED.init(128, 64)
basic.forever(function () {
	
})

```

## Étape 3

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||loops: chaque 500 ms ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```blocks

let Celsius = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
})

```

## Étape 4

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P2||``.

```blocks

let Celsius = 0
loops.everyInterval(500, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 5

Modifie le bloc ``||loops: chaque 500 ms||``.

Remplace la valeur ``||loops: 500||`` par ``||loops: 2000||``.

```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 6

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) sous le bloc ``||variables: définir Celsius ||``.

```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
})

```

## Étape 7

Ajoute le bloc ``||OLED:show string||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED display ||`` (trad. : effacer l'écran).

Remplace la valeur ``||OLED:" "||`` par le bloc ``||text: concaténation ||``.

```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeStringNewLine("Bonjour" + "Monde")
})

```

## Étape 8

Modifie le bloc ``||text: concaténation ||``.

Appuie sur le ``||text: + ||`` du bloc ``||text: concétanation ||`` pour ajouter un espace supplémentaire.

Remplace la valeur ``||text: Bonjour ||`` par ``||text: Celsius ||``.

Remplace la valeur ``||text: Monde ||`` par ``||text: : ||``.

Remplace la valeur ``||text: " " ||`` par le bloc ``||variables: Celcius||``.


```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
})


```

## Étape 9

Ajoute le bloc ``||logic:si vrai alors sinon||`` dans le bloc ``||basic: toujours ||``.


```blocks

basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})

```

## Étape 10

Modifie le bloc ``||logic:si vrai alors sinon||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:20||``.


```blocks

let Celsius = 0
basic.forever(function () {
    if (Celsius > 20) {
    	
    } else {
    	
    }
})

```

## Étape 11

Ajoute le bloc``|| pins: écrire sur la broche ||`` dans le bloc ``||logic:si||``.

Remplace la valeur ``|| pins: P0 ||`` par ``|| pins: P16 ||``.

Remplace la valeur ``|| pins: 0 ||`` par ``|| pins: 1 ||``.

```blocks

let Celsius = 0
basic.forever(function () {
    if (Celsius > 20) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
    	
    }
})

```

## Étape 12

Ajoute le bloc``|| pins: écrire sur la broche ||`` dans le bloc ``||logic:sinon||``.

Remplace la valeur ``|| pins: P0 ||`` par ``|| pins: P16 ||``.

La valeur ``|| pins: 0 ||`` demeure la même.

```blocks

let Celsius = 0
basic.forever(function () {
    if (Celsius > 20) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
})

```

## Étape 13

Voici la programmation complète du programme.


```blocks

let Celsius = 0
led.enable(false)
OLED.init(128, 64)
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
})
basic.forever(function () {
    if (Celsius > 20) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.