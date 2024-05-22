# ElecFreaks micro:bit Smart Home Kit

# Tutoriel supplémentaire - A

## @showdialog

Invente une programmation.

## Étape 1

Utilise le plus de blocs possibles.

Bonne chance !

```package

dstemps=github:tinkertanker/pxt-smarthome

```

```blocks

let Celsius = 0
let Lumen = 0
let strip: neopixel.Strip = null
OLED.clear()
led.enable(false)
OLED.init(128, 64)
OLED.writeStringNewLine("Bonjour" + "Monde")
loops.everyInterval(500, function () {
    basic.pause(100)
})
basic.forever(function () {
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
    strip = neopixel.create(DigitalPin.P0, 1, NeoPixelMode.RGB)
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.