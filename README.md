# Satellite Link Budget Calculator

A GEO downlink link budget calculator written in Python.
Built as a self-study project while transitioning into
satellite communications engineering.

## What it calculates

Given 7 input parameters, the calculator computes:

- Transmit power - converts Watts to dBW
- EIRP - Effective Isotropic Radiated Power (dBW)
- Free Space Path Loss - using the standard FSPL formula
- Received signal power - at the ground station antenna
- Noise power - using Boltzmann's constant, noise temperature and bandwidth
- C/N ratio - Carrier to Noise ratio (dB)
- Link status - whether the link closes against a 5.5 dB QPSK threshold

## Inputs required

| Parameter | Unit |
|---|---|
| Transmit power | Watts |
| Transmit antenna gain | dBi |
| Frequency | GHz |
| Distance to satellite | km |
| Receive antenna gain | dBi |
| System noise temperature | Kelvin |
| Bandwidth | MHz |

## Formula used

Convert watts to dBW, 
power_dbw (dBW) = 10 * math.log10(power_w)

Free Space Path Loss, 
FSPL (dB) = 92.4 + 20 * math.log10(freq_ghz) + 20 * math.log10(dist_km)

Effective Isotropic Radiated Power, 
EIRP (dBW) = power_dbw + gain_tx

Received signal power
power_rx = eirp - fspl + gain_rx 

Noise power, 
Noise_power (dBW) = 10 * math.log10(1.38e-23 * noise_temp * bandwidth * 1e6)

Carrier to Noise ratio, 
C/N (dB) = power_rx - noise_power


