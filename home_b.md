# ElecFreaks micro:bit Smart Home Kit

# Tutoriel supplémentaire - B

## @showdialog

Invente une programmation. Les blocs ont été placés dans le désordre.

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
let strip: neopixel.Strip = null
let Celsius = 0
let Lumen = 0
led.enable(false)
OLED.init(128, 64)
OLED.clear()
OLED.drawLoading(Lumen)
if (true && true) {
	
}
OLED.writeStringNewLine("Celsius")
OLED.writeNumNewLine(Celsius)
if (true || true) {
	
}
strip.showColor(neopixel.colors(NeoPixelColors.Black))
basic.pause(100)
music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
music.setVolume(100)
strip = neopixel.create(DigitalPin.P1, 1, NeoPixelMode.RGB)
Celsius = smarthome.ReadTemperature(TMP36Type.TMP36_temperature_C, AnalogPin.P2)
Lumen = smarthome.ReadLightIntensity(AnalogPin.P3)
basic.forever(function () {
	
})
loops.everyInterval(1000 * 5, function () {
	
})

```

## @showdialog 

Félicitations! Tu as terminé la programmation. Réalise maintenant les branchements.

Pour tester le circuit électrique, télécharge la programmation dans le micro:bit.