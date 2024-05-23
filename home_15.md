# ElecFreaks micro:bit Smart Home Kit

# Tutoriel 15

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


```blocks

led.enable(false)
OLED.init(128, 64)

```

## Étape 3

Ajoute le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse) de l'onglet ``||neopixel:  neopixel ||`` sous le bloc ``||OLED: initialize OLED ||`` (trad. : démarrer l'écran).

Modifie le bloc ``||variables:  définir strip ||``.

Remplace la valeur ``||neopixel:  P0 ||`` par ``||neopixel:  P1 ||``.

Remplace la valeur ``||neopixel:  24 ||`` par  ``||neopixel:  1 ||``.

La valeur ``||neopixel:  RGB ||`` demeure la même.


```blocks

led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
})

```

## Étape 4

Ajoute le bloc ``||neopixel:  régler couleur||`` sous le bloc ``||variables:  définir strip ||`` (trad. : bande lumineuse).

Remplace la valeur ``||neopixel:  rouge ||`` par la valeur ``||neopixel:  noir||``.

```blocks

led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))

```

## Étape 5A

Glisse le bloc ``||loops: chaque 500 ms||`` dans la zone de programmation.

Remplace la valeur ``||loops: 500||`` par ``||loops: 2000||``.

```blocks

loops.everyInterval(2000, function () {
	
})

```
## Étape 5B

Crée une ``||variables: variable||`` et donne-lui le nom ``||variables:Celsius||``.

Ajoute le bloc ``||variables: définir Celsius ||`` dans le bloc ``||loops: chaque||``.

Remplace la valeur ``||variables:0||`` par le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
})


```

## Étape 5C

Modifie le bloc ``||smarthome:value of temperature||`` (trad. : la valeur de la température).

La valeur ``||smarthome:C||`` demeure la même.

Remplace la valeur ``||smarthome:P1||`` par ``||smarthome:P2||``.


```blocks

let Celsius = 0
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
})

```

## Étape 6

Ajoute le bloc ``||OLED:clear OLED display||`` (trad. : effacer l'écran) dans le bloc ``||loops: chaque ||``.

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

Ajoute le bloc ``||logic:si vrai alors ||`` dans le bloc ``||basic: toujours ||``.


```blocks

basic.forever(function () {
    if (true) {
    	
    }
})


```

## Étape 10

Modifie le bloc ``||logic:si vrai alors||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 < 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:21||``.

```blocks

let Celsius = 0
basic.forever(function () {
       if (Celsius < 21) {
    	
    }
})

```

## Étape  11

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:si||``.

Modifie la valeur ``||neopixel: rouge ||`` par la valeur ``||neopixel: jaune ||``.

```blocks

let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0
basic.forever(function () {
      if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
})


```

## Étape 12

Ajoute le bloc ``||logic:si vrai alors ||`` sous le bloc ``||logic: si vrai alors ||``.

```blocks

let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0
basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (true) {
    	
    }
})


```

## Étape 13

Modifie le bloc ``||logic:si vrai alors||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:et||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:0 < 0||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (0 > 0 && 0 < 0) {
    	
    }
})


```

## Étape 14

Modifie le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:22||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && 0 < 0) {
    	
    }
})


```

## Étape 15

Modifie le bloc ``||logic:0 < 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:25||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
    	
    }
})

```

## Étape 16

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:si||``.

Modifie la valeur ``||neopixel: rouge ||`` par la valeur ``||neopixel: orange ||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
        strip.showColor(neopixel.colors(NeoPixelColors.Orange))
    }
})

```

## Étape 17

Ajoute le bloc ``||logic:si vrai alors ||`` sous le bloc ``||logic: si vrai alors ||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
        strip.showColor(neopixel.colors(NeoPixelColors.Orange))
    }
    if (true) {
    	
    }
})

```

## Étape 16

Modifie le bloc ``||logic:si vrai alors||``.

Remplace la valeur ``||logic:vrai||`` par le bloc ``||logic:0 > 0||``.

Remplace la valeur ``||logic:0||`` de gauche par le bloc ``||variables:Celsius||``.

Remplace la valeur ``||logic:0||`` de droite par la valeur ``||logic:26||``.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
        strip.showColor(neopixel.colors(NeoPixelColors.Orange))
    }
    if (Celsius > 26) {
    	
    }
})


```

## Étape 17

Ajoute le bloc ``||neopixel:  régler couleur||`` dans le bloc ``||logic:si||``.

La valeur ``||neopixel: rouge ||`` demeure la même.

```blocks
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
let Celsius = 0

basic.forever(function () {
    
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
        strip.showColor(neopixel.colors(NeoPixelColors.Orange))
    }
    if (Celsius > 26) {
        strip.showColor(neopixel.colors(NeoPixelColors.Red))
    }
})

```

## Étape 20

Voici la programmation complète du programme.

```blocks

let Celsius = 0
led.enable(false)
OLED.init(128, 64)
let strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
strip.showColor(neopixel.colors(NeoPixelColors.Black))
loops.everyInterval(2000, function () {
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
    OLED.writeStringNewLine("Celsius" + ":" + Celsius)
})
basic.forever(function () {
    if (Celsius < 21) {
        strip.showColor(neopixel.colors(NeoPixelColors.Yellow))
    }
    if (Celsius > 22 && Celsius < 25) {
        strip.showColor(neopixel.colors(NeoPixelColors.Orange))
    }
    if (Celsius > 26) {
        strip.showColor(neopixel.colors(NeoPixelColors.Red))
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.