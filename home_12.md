# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 12

## @showdialog

Utilise l'écran OLED, les capteurs, le bouclier d'extension et les câbles.


## Étape 1

Supprime le bloc ``||basic:toujours||``.

```package

dstemps=github:tinkertanker/pxt-smarthome

```

## Étape 2

Ajoute le bloc ``|| pins: écrire sur la broche ||`` dans le bloc ``||basic:au démarrage||``.

```blocks

pins.digitalWritePin(DigitalPin.P0, 0)

```

## Étape 3

Modifie le bloc ``|| pins: écrire sur la broche ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P16 ||``.

La valeur ``|| pins: 0 ||`` demeure la même.

```blocks

pins.digitalWritePin(DigitalPin.P16, 0)

```

## Étape 4

Ajoute le bloc ``||smarthome:setup crash sensor||`` (trad. : paramétrer le capteur d'impact) sous le bloc ``|| pins: écrire sur la broche ||``.

Remplace la valeur ``||smarthome:P0||`` par ``||smarthome:P5||``.

```blocks

pins.digitalWritePin(DigitalPin.P16, 1)
smarthome.crashSensorSetup(DigitalPin.P5)

```

## Étape 5

Ajoute le bloc ``||logic:si vrai alors sinon||`` dans le bloc ``|| basic: toujours ||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||smarthome:crash sensor pressed||`` (trad. : capteur d'impact pressé).

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
    	
    } else {
    	
    }
})

```

## Étape 6

Ajoute le bloc ``|| pins: écrire sur la broche ||`` dans le bloc ``||logic:si||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P16 ||``.

Remplace la broche ``|| pins: 0 ||`` par ``|| pins : 1 ||``.

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
    	
    }
})

```

## Étape 7

Ajoute le bloc ``|| pins: écrire sur la broche ||`` dans le bloc ``||logic:sinon||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins : P16 ||``.

La valeur ``|| pins: 0 ||`` demeure la même.

```blocks

basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
})

```

## Étape 8

Voici la programmation complète du programme.

```blocks

pins.digitalWritePin(DigitalPin.P16, 1)
smarthome.crashSensorSetup(DigitalPin.P5)
basic.forever(function () {
    if (smarthome.crashSensor()) {
        pins.digitalWritePin(DigitalPin.P16, 1)
    } else {
        pins.digitalWritePin(DigitalPin.P16, 0)
    }
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.