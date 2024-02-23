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

input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.AB, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let Celsius = 0
let Lumen = 0
let strip: neopixel.Strip = null
led.enable(false)
OLED.init(128, 64)
basic.pause(100)
OLED.writeStringNewLine("microbit")
OLED.writeNumNewLine(0)
basic.forever(function () {
    strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
    strip.showColor(neopixel.colors(NeoPixelColors.Red))
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
    OLED.clear()
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
    OLED.clear()
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.