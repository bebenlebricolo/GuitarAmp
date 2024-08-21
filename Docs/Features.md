# Guitar amplifier features
This amp will be a hybrid all-hardware/modelisation solid state amplifier.

# Various I/O configurations
* Effects (send and return) loop
  * Send signal is picked up right before the power amplifier (hence after EQ, distortion and internal effects) to benefit from the whole transformation chain of the amplifier.
  * Return is mixed with the normal signal right before the power amplifier. Linear mixing is used (blending) and no further transformation is applied to it before entering the power stage.
    * This topology allows the devices in the effect loop to get the signal after being affected by the first stages of the amp, such as the preamp, etc. Mainly, this is very useful when recording the signal (like with a looper pedal), so that the user can switch to a different amp config (like switch back from dist channel to clean channel) and still retain the character of the former setting.
* Line out / Phones out connector with selectable mute ability.
  * On many amps, the phones out connector mutes the amp automatically, but on stage it can be nice to use the amp as a stage monitor at the same time. Having a switch to manually mute the amp can be useful in such circumstances.
* Line in connector with blend pot : used on stage to blend in the global mix whilst keeping the guitar volume up when used as a stage monitor.
  * Can be used as an Auxiliary input channel as well

# Analogue hardware implementation
* Clean channel
  * Provide an always clean channel, with a simple volume knob
* Distortion channels :
  * Several distortions can be selected with a commutator (rotary selector ?)
    * Tube screamer style (some sort of soft clipping)
    * Blues breaker style (some sort of soft clipping)
    * Boss DS1 style (hard clipping)
    * Fuzz style (hard clipping)
    * All distortions can be blended with the clean channel pot (parallel distortion)
* A simple tonestack to rule them all right after the buffer stage.

# Common output
* Class D power amplifier (targeting various output electrical powers 20W/40W/100W - same preamp, different versions)
  * Very compact, powerful and efficient solution vs class AB amps. Very low Total Harmonic Distortion as well
  * [IR4301 from Infineon - 160W max in 4Ohms speaker.](https://www.infineon.com/cms/en/product/power/class-d-audio-amplifier-ic/integrated-class-d-audio-amplifier-ics/ir4301m/)
  * [TPA3221 from Texas Instrument - 200W max Mono](https://www.ti.com/product/TPA3221?bm-verify=AAQAAAAJ_____8bHEyi1lknqwZMIK6qVq0QrxOSri5pRLfE5Tx8Ei92xOpDOnvyYqY0pJ1FBeCCcEe946BsfwUq8XGuiT53k1O60hmF5RD8iHPfye3fx_qNRCzHYdmPiyOwQVNzL0Gztm8i68DjWy1ZyGysiHlPsocx_32p2o8H022t-Gmhf9Iji0ypm-64rP8FcvTo75ap230wVQTNV73WaBVlUSAvAEyTXlfw43dRGek7XvF-TS61Pn0Zx5952Bnpsji4rOxRJkBtggb-YiabqLufzjApndIIxP8OEqCoamVDscUy72g9wkv9e8UMyh_GK)
* A master volume knob !!
* Footswitch that allows to quickly switch between channels and settings

# DSP based modelisation + MCU logic
This amp can be extended with a Digital Signal Process + Microcontroller to handle the logic.
Controls need to be doubled to use the same user interface : all pots need to be dual tracks :
* one track is directly inserted into the main analogue circuitry
* the other track is used to send an DC analogue voltage to the MCU

Bluetooth connectivity can be added with such a configuration.
All signals are blended right before the power amp, of course.

# Power supply
This amp will use a high frequency switch mode power supply to reduce weight and dissipated heat.
* Either of the shelf PSU or custom built (more expensive)