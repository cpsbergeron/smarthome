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

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Lumen||``.

Ajoute le bloc ``||variables: définir Lumen ||`` dans le bloc ``||loops: chaque 500 ms ||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value light||`` (trad. : la valeur de la luminosité).

```blocks

let Lumen = 0
loops.everyInterval(500, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
})

```

## Étape 4

Modifie le bloc ``||smarthome:value light||`` (trad. : la valeur de la luminosité).

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P3||``.

```blocks

let Lumen = 0
loops.everyInterval(500, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## Étape 5

Modifie le bloc ``||loops: chaque 500 ms||``.

Remplace la valeur ``||loops: 500||`` par ``||loops: 2000||``.

```blocks

let Lumen = 0
loops.everyInterval(2000, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
})

```

## Étape 6

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) sous le bloc ``||variables: définir Lumen ||``.

```blocks

let Lumen = 0
loops.everyInterval(2000, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
})

```

## Étape 7

Ajoute le bloc ``||OLED:show string||`` (trad. : montrer la ligne) sous le bloc ``||OLED: clear OLED display ||`` (trad. : effacer l'écran).

Remplace la valeur ``||OLED:" "||`` par le bloc ``||text: concaténation ||``.

```blocks

let Lumen = 0
loops.everyInterval(2000, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Bonjour" + "Monde")
})

```

## Étape 8

Modifie le bloc ``||text: concaténation ||``.

Appuie sur le ``||text: + ||`` du bloc ``||text: concétanation ||`` pour ajouter un espace supplémentaire.

Remplace la valeur ``||text: Bonjour ||`` par ``||text: Lumen ||``.

Remplace la valeur ``||text: Monde ||`` par ``||text: : ||``.

Remplace la valeur ``||text: " " ||`` par le bloc ``||variables: Lumen||``.


```blocks

let Lumen = 0
loops.everyInterval(2000, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
    OLED.clear()
    OLED.writeStringNewLine("Lumen" + ":" + Lumen)
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

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 < 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Lumen||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:100||``.


```blocks

let Lumen = 0
basic.forever(function () {
    if (Lumen < 100) {
    	
    } else {
    	
    }
})

```

## Étape 11

Ajoute le bloc ``|| pins: régler position du servo ||`` dans le bloc ``||logic:si||``.

Remplace la valeur ``|| pins: P0 ||`` par ``|| pins: P8 ||``.

La valeur ``|| pins: 180 ||`` demeure la même.

```blocks

let Lumen = 0
basic.forever(function () {
    if (Lumen < 100) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
    	
    }
})

```

## Étape 12

Ajoute le bloc ``|| pins: régler position du servo ||`` dans le bloc ``||logic:sinon||``.

Remplace la valeur ``|| pins: P0 ||`` par ``|| pins: P8 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins: 0 ||``.

```blocks

let Lumen = 0
basic.forever(function () {
    if (Lumen < 100) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})

```

## Étape 13

Voici la programmation complète du programme.


```blocks

let Lumen = 0
led.enable(false)
OLED.init(128, 64)
loops.everyInterval(2000, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
    OLED.clear()
    OLED.writeStringNewLine("Lumen" + ":" + Lumen)
})
basic.forever(function () {
    if (Lumen < 100) {
        pins.servoWritePin(AnalogPin.P8, 180)
    } else {
        pins.servoWritePin(AnalogPin.P8, 0)
    }
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.