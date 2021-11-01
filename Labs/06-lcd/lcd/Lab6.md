# Lab 6: Ozan Dinc

https://github.com/Ozansio/Digital-Electronics-2/new/main/Labs/06-lcd/lcd


### LCD display module

1. In your words, describe what ASCII table is.
   * ASCII
   * The ASCII table contains letters, numbers, control characters, and other symbols. Each character is assigned a unique 7-bit
code. ASCII is an acronym for American Standard Code for Information Interchange.

2. (Hand-drawn) picture of time signals between ATmega328P and LCD keypad shield (HD44780 driver) when transmitting three character data `De2`.

![WhatsApp Image 2021-11-01 at 23 41 52](https://user-images.githubusercontent.com/91128854/139753176-76f3bd09-434d-4a7c-bc76-46ae8cecf141.jpeg)

### Stopwatch

1. Flowchart figure for `TIMER2_OVF_vect` interrupt service routine which overflows every 16&nbsp;ms but it updates the stopwatch LCD approximately every 100&nbsp;ms (6 x 16&nbsp;ms = 100&nbsp;ms). Display tenths of a second and seconds `00:seconds.tenths`. Let the stopwatch counts from `00:00.0` to `00:59.9` and then starts again. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.

  ![WhatsApp Image 2021-11-01 at 23 41 52 (1)](https://user-images.githubusercontent.com/91128854/139753287-c38edc42-3e2e-4ff0-a006-caaaa66806eb.jpeg)

### Custom characters

1. Code listing with syntax highlighting of two custom character definition:
```c
/* Variables ---------------------------------------------------------*/
// Custom character definition using https://omerk.github.io/lcdchargen/
byte customChar[16] = {
	0b00000,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b00000,
  0b00000,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b01110,
	0b00000
};

```

### Kitchen alarm

Consider a kitchen alarm with an LCD, one LED and three push buttons: start, +1 minute, -1 minute. Use the +1/-1 minute buttons to increment/decrement the timer value. After pressing the Start button, the countdown starts. The countdown value is shown on the display in the form of mm.ss (minutes.seconds). At the end of the countdown, the LED will start blinking.

1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.

   ![WhatsApp Image 2021-11-01 at 23 41 52 (2)](https://user-images.githubusercontent.com/91128854/139753741-f752a20f-a002-49d6-a4eb-7b3c3db245dc.jpeg)

