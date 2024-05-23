# ElecFreaks micro:bit Smart Home Kit

# Tutoriel supplémentaire - B

## @showdialog

Invente une programmation. Les blocs ont été placés dans le désordre.

## Étape 1

Utilise le plus de blocs possible.

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
strip.showColor(neopixel.colors(NeoPixelColors.Red))
basic.pause(0 * 0)
music.setVolume(127)
smarthome.crashSensorSetup(DigitalPin.P0)
pins.digitalWritePin(DigitalPin.P0, 0)
pins.servoWritePin(AnalogPin.P0, 180)
loops.everyInterval(500, function () {
    Lumen = smarthome.ReadLightIntensity(AnalogPin.P1)
    Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P1)
    strip = neopixel.create(DigitalPin.P0, 1, NeoPixelMode.RGB)
})
basic.forever(function () {
    if (0 < 0) {
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.Dadadadum), music.PlaybackMode.InBackground)
    }
    if (smarthome.crashSensor()) {
    	
    }
})


```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.