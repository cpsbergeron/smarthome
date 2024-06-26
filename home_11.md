# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 11

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.


## Étape 11

Ajoute le bloc ``|| pins: régler position servo ||`` dans le bloc ``||basic:au démarrage||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

pins.servoWritePin(AnalogPin.P0, 180)

```

## Étape 2

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 0 ||``.

```blocks

pins.servoWritePin(AnalogPin.P8, 0)

```

## Étape 3

Ajoute le bloc ``||smarthome:setup crash sensor||`` (trad. : paramétrer le capteur d'impact) sous le bloc ``|| pins: régler position servo ||``.

Remplace la valeur ``||smarthome:P0||`` par ``||smarthome:P5||``.

```blocks

pins.servoWritePin(AnalogPin.P8, 0)
smarthome.crashSensorSetup(DigitalPin.P5)

```

## Étape 4

Ajoute le bloc ``||logic:si vrai alors||`` dans le bloc ``|| basic: toujours ||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||smarthome:crash sensor pressed||`` (trad. : capteur d'impact pressé).

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
    	
    }
})

```

## Étape 5

Ajoute le bloc ``|| pins: régler position servo ||`` sous le bloc ``||smarthome:crash sensor pressed||`` (trad. : capteur d'impact pressé).

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

La la valeur ``|| pins: 180 ||`` demeure la même.

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.servoWritePin(AnalogPin.P8, 180)
    }
})

```

## Étape 6

Ajoute le bloc ``|| basic: pause ||`` sous le bloc ``|| pins: régler position servo ||``.

Remplace la valeur ``|| basic: 100 ||`` par ``|| basic: 2500 ||``.

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.servoWritePin(AnalogPin.P8, 180)
        basic.pause(2500)
    }
})

```

## Étape 7

Ajoute le bloc ``|| pins: régler position servo ||`` sous le bloc ``|| basic: pause ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 0 ||``.

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.servoWritePin(AnalogPin.P8, 180)
        basic.pause(2500)
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})

```

## Étape 8

Voici la programmation complète du programme.


```blocks

pins.servoWritePin(AnalogPin.P8, 0)
smarthome.crashSensorSetup(DigitalPin.P5)
basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.servoWritePin(AnalogPin.P8, 180)
        basic.pause(2500)
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.