---
layout: post
title: "CWNA Chapter 2: RF Characteristics and Behaviors"
date: "2018-05-07 23:51:42 -0400"
---

Chapter 2 is an introduction to basic RF concepts.

## Objectives

* Define/explain basic characteristics of RF and RF behavior

## Electromagnetic Waves

* A **wave** is motion that travels through matter and space
* An **electromagnetic wave** is an oscillation that travels through space, and can even travel in a vacuum devoid of matter
* An **electric field** is the space in which an electrically charged object "feels" a push or pull (depending on whether the charge is like or opposite)
  * The strength of an electric field is measured as the force induced on a unit of electric charge at any given point within the field
* A **magnetic field** is produced by the moving electric charge that is present around a magnet or in free space
  * A changing magnetic field creates an electric field; this is key for the propagation of radio frequencies
* **Radio frequency propagation** describes the way in which waves move through space; electric fields create magnetic fields and vice versa
* **Electromagnetic waves** a combination of electric and magnetic fields propagating through space; the two fields oscillate perpendicular to each other
* A **Radio Frequency (RF)** system relies on electromagnetic wave theory to provide a communications system
* **Modulation** describes the manipulation of an electromagnetic wave to represent data

## RF Characteristics and Behaviors

* **Wavelength** is the distance between two identical points on the wave (that are adjacent)...i.e. from peak to peak or trough to trough.
  * Wavelength is a critical factor; dictates receiving antenna size and how the wave will interact with its environment
  * Wavelength is related to the frequency and the speed of light; so, if you have frequency you can calculate wavelenght and vice versa.
* The **hertz** unit refers to the number of cycles a wave generates in a second
  * kilohertz = 1,000 hertz, megahertz is 1,000,000 hertz and gigahertz is 1,000,000,000 hertz
* The following formula (where \\(\lambda\\) is wavelength in meters, \\(f\\) is frequency in hertz and \\(c\\) is the speed of light in a vacuum) can be used to calculate wavelength and frequency:

$$\lambda = c/f$$

* The following simpler formulas can be used for approximations and are sufficient for the WLAN administrator:

$$\lambda (inches) = 11.811 / f (GHz)$$

$$\lambda (cm) = 30 / f (GHz)$$

The following table shows Wi-Fi wavelengths for the first US channels available in 2.4 and 5 GHz. These were calculated using the approximations described above.

![Wi-Fi Channel wavelengths]({{"/images/wifi-wavelengths.png" | absolute_url}})

* Note the wavelength for the 5 GHz channel is approximately half that of the 2.4 GHz channel; this greatly affects the receptivity of 5 GHz channels at greater distances

* **Frequency** refers to the number of wave cycles occurring in a certain window of time (usually 1 second)
  * So, 1 kilohertz is 1,000 cycles of a wave in one second
  * Wavelength, frequency and medium are interdependent; the higher frequencies will have the shorter wavelengths, whereas lower frequencies will have the longer wavelengths
  * By using different frequencies, distinct RF connections can be made available in a given coverage area (or cell)
  * If frequencies are used that are not sufficiently spaced apart, they will interfere with each other (like hitting 6 or 7 adjacent keys on a piano keyboard)
  * **Modulation** describes the process in which a carrier is manipulated to represent meaningful information (or data)
    * **Frequency Shift Keying (FSK)**, altering the frequency to represent data, is used by some wireless systems (but not WLANs)

* **Amplitude** is the characteristic that describes "volume";
    * A "loud" RF wave with higher amplitude is easier to detect than a "quiet" one with lower amplitude
    * A wave with greater amplitude is easier to detect at greater distance than one that starts with lower amplitude
    * **Noise Floor** describes the continual backround RF noise present in a specific location, usually higher in 2.4 GHz and 5 GHz; high noise floor reduces the ability to achieve higher data rates
    * An increase in amplitude will generally extend the "range" of an RF wave, but simply increasing output power will not necessarily be an improvement. If clients can't match the output power, they might not be able transmit a signal to the access point. So, higher gain antennas or additional access points are usually a better solution.
    * **Amplitude Shift Keying (ASK)** is a modulation technique involving changing the amplitude of a wave; this is used in WLANs
    * **Quadrature Amplitude Modulation (QAM)** employs ASK and other modulation techniques

* **Phase** is a comparison between two RF waves; in-phase waves will strengthen each other and out-of-phase waves will cancel each other out
  * Phase is measured in degrees, with 180 degrees being completely out of phase and 0 degrees being completely in phase
  * In a practical sense for a CWNA, waves are usually simply in-phase or out-of-phase
  * In-phase waves can increase the strength of a received signal, but it will never be stronger than the transmitted signal (since waves always weaken as they travel through space)
  * **Multiple-input-multiple-output (MIMO)** takes advantage of the multiple paths a signal can travel to multiple antennas in slightly different locations in the transmitter and receiver devices; multiple paths produce waves that are usually a bit out of phase as a result of reflection or scattering
  * **Phase Key Shifting (PSK)** shifts the phase of waves as a modulation technique; 802.11 WLANs use both PSK and ASK
  


_Notes are based on the Certitrek Certified Wireless Network Administrator Official Study Guide (Tom Carpenter and Mitch Dickey)._
