# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 12

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.


## Étape 1

Supprime le bloc ``||basic:toujours||``.

## Étape 2

Ajoute le bloc ``|| pins: écrire sur la broche ||`` dans le bloc ``||basic:au démarrage||``.

```blocks

pins.digitalWritePin(DigitalPin.P0, 0)

```

## Étape 3

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

La valeur ``|| pins: 0 ||`` demeure la même.

```blocks

pins.digitalWritePin(DigitalPin.P12, 0)

```

## Étape 4

Ajoute le bloc pause ``|| basic: pause (ms) ||`` dans le bloc ``||input:lorsque le bouton A est pressé||``.

La valeur ``|| basic: 100 ||`` du bloc ``|| basic: pause (ms) ||`` demeure la même.

Ajoute le bloc ``|| pins: écrire sur la broche ||``  sous le bloc  ``|| basic: pause (ms) ||``.

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P0, 0)
})


```

## Étape 5

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

Remplace la valeur ``|| pins: 0 ||`` par ``|| pins : 1 ||``.

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P12, 1)
})


```

## Étape 6

Ajoute le bloc pause ``|| basic: pause (ms) ||`` dans le bloc ``||input:lorsque le bouton B est pressé||``.

La valeur ``|| basic: 100 ||`` du bloc ``|| basic: pause (ms) ||`` demeure la même.

Ajoute le bloc ``|| pins: écrire sur la broche ||``  sous le bloc  ``|| basic: pause (ms) ||``.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P0, 0)
})


```

## Étape 7

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P12 ||``.

La valeur ``|| pins: 0 ||`` demeure la même.

```blocks

input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P12, 0)
})


```

## Étape 8

Voici la programmation complète du programme.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

input.onButtonPressed(Button.A, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P12, 1)
})
input.onButtonPressed(Button.B, function () {
    basic.pause(100)
    pins.digitalWritePin(DigitalPin.P12, 0)
})
pins.digitalWritePin(DigitalPin.P12, 0)

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.