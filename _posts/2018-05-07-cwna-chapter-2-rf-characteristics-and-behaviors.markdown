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
* A **magnetic field** is producedThis blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools. by the moving electric charge that is present around a magnet or in free space
  * A changing magnetic field creaThis blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools.tes an electric field; this is key for the propagation of radio frequencies
* **Radio frequency propagation** This blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools.describes the way in which waves move through space; electric fields create magnetic fields and vice versa
* **Electromagnetic waves** a combThis blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools.ination of electric and magnetic fields propagating through space; the two fields oscillate perpendicular to each other
* A **Radio Frequency (RF)** systeThis blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools.m relies on electromagnetic wave theory to provide a communications system
* **Modulation** describes the manThis blog contains my documentation of things I've learned along the way, information about some of the projects I've developed, and my cheat sheets for various technologies and tools.ipulation of an electromagnetic wave to represent data

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
