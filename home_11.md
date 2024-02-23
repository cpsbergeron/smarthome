# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 11

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.


## Étape 1

Supprime le bloc ``||basic:toujours||``.

## Étape 2

Ajoute le bloc ``|| pins: régler position servo ||`` dans le bloc ``||basic:au démarrage||``.

```blocks

pins.servoWritePin(AnalogPin.P0, 180)

```

## Étape 3

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 0 ||``.

```blocks

pins.servoWritePin(AnalogPin.P8, 0)

```

## Étape 4

Ajoute le bloc pause ``|| basic: pause (ms) ||`` dans le bloc ``||input:lorsque le bouton A est pressé||``.

La valeur ``|| basic: 100 ||`` du bloc ``|| basic: pause (ms) ||`` demeure la même.

Ajoute le bloc ``|| pins: régler position servo ||``  sous le bloc  ``|| basic: pause (ms) ||``.

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P0, 180)
})

```

## Étape 5

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 90 ||``.

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 90)
})

```

## Étape 6

Ajoute le bloc pause ``|| basic: pause (ms) ||`` dans le bloc ``||input:lorsque le bouton B est pressé||``.

La valeur ``|| basic: 100 ||`` du bloc ``|| basic: pause (ms) ||`` demeure la même.

Ajoute le bloc ``|| pins: régler position servo ||``  sous le bloc  ``|| basic: pause (ms) ||``.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P0, 180)
})

```

## Étape 7

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

La valeur ``|| pins: 180 ||`` demeure la même.
```blocks

input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 180)
})

```

## Étape 8

Ajoute le bloc pause ``|| basic: pause (ms) ||`` dans le bloc ``||input:lorsque le bouton A+B est pressé||``.

La valeur ``|| basic: 100 ||`` du bloc ``|| basic: pause (ms) ||`` demeure la même.

Ajoute le bloc ``|| pins: régler position servo ||``  sous le bloc  ``|| basic: pause (ms) ||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P0, 180)
})

```

## Étape 9

Modifie le bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins : 0 ||``.

```blocks

input.onButtonPressed(Button.AB, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 0)
})

```

## Étape 10

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 90)
})
input.onButtonPressed(Button.AB, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 0)
})
input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.servoWritePin(AnalogPin.P8, 180)
})
pins.servoWritePin(AnalogPin.P8, 0)

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.