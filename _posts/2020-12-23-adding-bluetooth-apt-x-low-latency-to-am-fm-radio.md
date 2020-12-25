---
tags:
- electronics
- bluetooth
title: Adding Bluetooth Apt-X Low Latency to AM/FM radio
published: false

---
# Goal

The mission: integrate a bluetooth Apt-X Low Latency receiver into an AM/FM portable radio to use for watching TV (with a matching Apt-X Low Latency Transmitter); do it in a few hours' of effort using on-hand materials.

![](/uploads/bt-radio-final.jpg)

I had a Panasonic RF-2400D, which is a fabulously simple audio device - it receives AM and FM radio. However, I wanted a higher-quality audio that a pretty terrible portable speaker I had been using for watching TV. The proposal was to integrate a Bluetooth Apt-X Low Latency receiver (BT-Rx) into this radio. A few problems needed to be solved:

* Find the line-out audio signal from the RF processing chip
  * Engineer a solution to multiplex the AM/FM signal and the line-out from the BT Rx to the audio amplifier.
* Combine stereo output from Bluetooth to mono
* Adapt the existing power sources to permanently power the BTRx
* Physically mount the BTRx

In short, all these things were done, although the power adaption took a few tries.

## Stereo to Mono

I had a spare 3.5mm plug. To this, I used two 470 ohm resistors on each channel, attached together to form the single output signal from the BTRx. For more details, see examples, such as at: [https://www.instructables.com/Simple-Way-to-Convert-Stereo-to-Mono/](https://www.instructables.com/Simple-Way-to-Convert-Stereo-to-Mono/ "https://www.instructables.com/Simple-Way-to-Convert-Stereo-to-Mono/")

## Audio Signal Multiplexing

I'll skip right to the good part.. investigating the circuit board. The heart of the RF audio processing seems to be a Silicon Labs am/fm series chip.  While I couldn't parse the chip markings exactly, the chip pinout and function seem very close to Si4831 [https://www.silabs.com/documents/public/data-sheets/Si4831-35-B30.pdf](https://www.silabs.com/documents/public/data-sheets/Si4831-35-B30.pdf "https://www.silabs.com/documents/public/data-sheets/Si4831-35-B30.pdf")

Other links:

[https://www.silabs.com/support/resources.p-audio-and-radio_multi-band-radios_si4820-24-25-31-35-36](https://www.silabs.com/support/resources.p-audio-and-radio_multi-band-radios_si4820-24-25-31-35-36 "https://www.silabs.com/support/resources.p-audio-and-radio_multi-band-radios_si4820-24-25-31-35-36")

![](/uploads/pxl_20201212_181434846-2.jpg)

Looking at the spec sheet, the two channels of audio output are pins 23 and 24. These signals trace through SMD resistors and combine similar to the 3.5mm plug above. Further tracing shows this signal enters the volume potentiometer. Bingo.

The plan is to:

* cut the trace of this mono-signal from the Si chip,
* attach wire to original trace and to a switched terminal of a SPDT slide switch.
* Attach BTRx output to other switched terminal
* Attach wire from common terminal of SPDT to volume potentiometer.

![](/uploads/switch-schematic.svg)

In the photo below, the PCB trace in blue is the original audio signal from RF IC to volume potentiometer. the small red line is where I cut the PCB with a hobby (Xacto) knife. The next photo shows the wires soldered on that lead to the switch.

![](/uploads/inkedaudio-trace-orig-annotated_li.jpg)

![](/uploads/audio-trace-zoom1.jpg)

## Other possible hacks

Note, that the RF IC and the PCB seem to have support for "Tone". One possibility is to add bass and treble controls.