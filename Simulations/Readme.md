# Simulations
Simulations are designed with LTSpice.

* Jfet_based_tonestack.asc : Fender style tonestack implementation using JFet as voltage controlled resistor (doesn't work)
* Mosfet_based_tonestack.asc : Fender style tonestack implementation using Mosfet as voltage controlled resistor (doesn't work neither)
* SoftClipAndCrossDist.asc : simulating different kinds of diode-based soft and hard clipping circuits.

# VCRs with FETs
It seems that VCRs (Voltage controlled resistors) are quite difficult to implement with FETs as their characteristics have quite a wide dispersion and :
* Gate to source/drain capacitance affects behavior upon gate voltage changing (current pulse are observed in high impedance parts of the circuit)
* The pseudo "linear" region is very small, very difficult to control precisely
* Floating resistor make its difficult to control : Vgs depends on what's connected on the source pin of the component. Hence if another Fet is used as a floating resistor, then Vgs is bootstrapped by what's following in the circuit.

=> Not very suitable to implement floating resistors.

## Motivation
Why trying to implement VCRs with FET ?
It would have been very nice to use a single potentiometer to feed to gate voltage of whatever VCR we have in place in the circuit.
Using such a topology allows to use the same potentiometers as an input for a DSP controller without having to use more expensive potentiometers (like double tracks), nor switch them with external circuitry (analog commutation) nor having double the amount of knobs..