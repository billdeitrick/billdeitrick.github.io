---
layout: post
title: "CWNA Chapter 1: WLAN and Networking Industry Organizations"
date: "2018-05-05 22:40:40 -0400"
---

## Objectives

* Understand how the 802.11 standards came about
* Understand who creates the standards
* Understand who manages the radio spectrum

## History of Wireless Communications

* Electromagnetic wave-based (or wireless) communications have been in use for decades
* The first wireless phone conversation took place in 1880; it was called the "Photophone" (used light as the medium) and communicated between rooftops (invented by Alexander Graham Bell)
* Guglielmo Marconi communicated wirelessly (an "S" was the first letter) across the Atlantic in the first decade of the twentieth century; this stirred government and commercial interest in wireless
* Mobile voice technology was perfected and used widely in the 1940s
* A **modem** modulates binary data into analog signals and demodulates the analog signals into binary data
* Early wireless devices were proprietary, so systems from different vendors could not communicate
* The **Institute of Electrical and Electronics Engineers (IEEE)** ratified the first **802.11** standard in **1997**; today this is called 802.11-Prime (1 or 2 Mbps data rates)
* **802.11a (54 Mbps)** and **802.11b (11 Mbps)** were ratified by the IEEE in **1999**


## Industry Organizations

* Three types: regulation (i.e. FCC), standardization (IEEE, IETF) and compatibility/certification (Wi-Fi alliance)
* Mass acceptance comes when regulation, standardization, and compatibility/certification work work together

## Regulatory Domain Government Agencies

* A **regulatory domain** is a geographic area controlled by a set of laws or policies
* In the United States, the Federal Communications Commission (FCC) is the manging Organization


### FCC

* **Hertz** is the specification for radio frequency; it is the measurement of wave cycles per second
* License-free bands for radio communications: **Industrial Scientific Medical (ISM)** and **Unlicensed National Information Infrastructure (UNII)**

| Frequency Band      | Total Band Width   | License-Free Band   |
|:-------------------:|:------------------:|:-------------------:|
| 2400 - 2500 MHz     | 100 MHz            | ISM                 |
| 5.15 - 5.25 GHz     | 100 MHz            | U-NII (U-NII-1)     |
| 5.25 - 5.35 GHz     | 100 MHz            | U-NII (U-NII-2A)    |
| 5.470 - 5.725 GHz   | 255 MHz            | U-NII (U-NII-2C)    |
| 5.725 - 5.850 GHz   | 100 MHz            | U-NII (U-NII-3)     |
{: .billtable}

* **Contention** is the process employed by 802.11 WLANs to access the medium for tansmission; this is a normal part of operations. Contention wait times become longer as more stations (STA) access the same channel.
* **Equivalent Isotropically Radiated Power (EIRP)** is a measurement of a system's output power after antenna gain
* A **Decibel (dB)** is a relative measurement of power, whereas a **dBm** is an absolute measure of power related to the Watt/milliWatt

### ITU-R

* The **International Telecommunications Union-Radiocommunication (ITU-R)** is part of the International Telecommunications Union, which is an agency of the United Nations tasked with providing worldwide leadership in Telecommunications
* The ITU-R maintains a database of frequency assignments worldwide and helps coordinate electromagnetic spectrum management in five regions:
  * A: The Americas
  * B: Western Europe
  * C: Eastern Europe
  * D: Africa
  * E: Asia and Australia

### IEEE

* The IEEE strives to be the world's leading professional association for the advancement of technology
* The organization creates many standards for niche areas within electronics and communications
* While several standards are important to the implementation and support of WLANs IEEE 802.11 is the primary standard
* The 802.11 standard has been amended many times since its inception; at any moment, it exists as "the standard as amended", which means that amendments, once ratified, become part of the standard.

### Wi-Fi Alliance

* The **Wi-Fi Alliance** is a certification organization that provides testing and interoperability analysis for the wireless industry
* Wi-Fi does not stand for "Wireless Fidelity" as some say; it is only a brand (marketing) name
* The Wi-Fi Alliance offers multiple types of certification programs and provides certificates for certified devices

### IETF

* The **Internet Engineering Task Force (IETF)** is another standards development organization that has had an influence on the wireless industry
  * **RFC 3748**: Extensible Authentication Protocol (EAP)
  * **RFC 2865**: Remote Access Dial-in User Service (RADIUS)
  * **RFC 5415**: Control and Provisioning of Wireless Access Points (CAPWAP) - replaces Lightweight Access Point Protocol (LWAPP)

### IEEE Standard Creation Process

* Projects managed by the IEEE, like the 802 project, are divided into working groups like 802.3 (Ethernet) and 802.11 (WLAN)
* A **PHY** is a physical communication layer
* The IEEE 802.11-1997 standard specified 3 PHYs: **Direct Sequence Spread Spectrum (DSSS)**, **Frequency Hopping Spread Spectrum (FHSS)**, and an Infrared PHY that was never used
* Updates to standards are added as amendments; while still in **draft** mode, they may be still be modified
* A **ratified** amendment is stable; after ratification software and hardware development will usually follow

#### 802.11 Amendments

| Amendment             | Description                                 |
|-----------------------|---------------------------------------------|
| 802.11a-1999          | Switch from DSSS to OFDM (Orthogonal Frequency Division Multiplexing). 5 GHz only, up to 54 Mbps. |
| 802.11b-1999          | High-Rate DSSS; 11 Mbps in 2.4 GHz |
| 802.11c-1998          | Updates to 802.1D bridging |
| 802.11d-2001          | Adds regulatory domains |
| 802.11e-2005          | Adds layer 2 MAC controls for QoS (supporting multimedia/voice) |
| 802.11g-2003          | DSSS, HR/DSSS, supported, OFDM in 2.4 GHz; up to 54 Mbps but incompatible with 5 GHz OFDM PHY |
| 802.11h-2003          | Adds Dynamic Frequency Selection (DFS) and Transmit Power Control (TPC) |
| 802.11i-2004          | Counter Mode Cipher Block Chaining Message Authentication Protocol (CCMP) (uses AES), provides for Temporal Key Integrity Protocol (TKIP) |
| 802.11j-2004          | 802.11 MAC/OFDM PHY can operate in 4.9-5 GHz in Japan/US |
| 802.11k-2008          | Allows use of TPC in frequencies other than 5 GHz and provides for reporting of client stats |
| 802.11n-2009          | Modifies physical and MAC layers for throughput of 600 Mbps (4 spatial streams, 40 MHz channels); 2.4 and 5 GHz |
| 802.11r-2008          | Fast roaming amendment; improve Basic Service Set transitions (BSS) withing Extended Service Sets (ESS) |
| 802.11s-2011          | Specifies ESS mesh network |
| 802.11u-2011          | Enable handoffs between WLANS and other types of networks |
| 802.11v-2011          | Improves radio management, adds standard SNMP MIBs |
| 802.11w-2009          | Enhances management frame security |
| 802.11-2007           | Rollup to bring all amendments into base document |
| 802.11-2012           | Rollup to bring all amendments into base document |
| 802.11ad-2012         | 60 GHz spec for Directional Multi-Gigabit (DMG) PHY |
| 802.11ae-2012         | Specifies management frame prioritization |
| 802.11ac-2013         | New PHY for 5 GHz (only); speeds gigabit and higher |
| 802.11af-2013         | Television Very High Throughput (TVHT) PHY |
| 802.11-2016           | Rollup to bring all amendments into base document, the most recent rollup |
| 802.11ah-2016         | < 1 GHz PHY, long range/low data rate (uses for IoT?) |

* 802.11-2016 is the most recent rollup of the 802.11 standard

#### IEEE Standards Impacting WLANs

* **IEEE 802.1X-2010**: port-based authentication/control for WLANS; critical for enterprise networks
* **IEEE 802.3-2015, Clause 33**: 802.3af/802.3at - PoE
* **IEEE 802.1D-2004**: bridging/priority handling (bridging, STP)
* **IEEE 802.1Q-2014**: priority tagging and VLAN handling for QoS

### Wireless Network Types

#### Wireless LANs

* **Mobility**: The network can be used while moving
* **Nomadic Ability**: Ability to move from place to place without active communications while moving
* **Fixed Connectivity**: No movement
* **Access Role**: the WLAN provides clients access to wired resouces; AP is fixed while clients may move
* **Distribution Role**: Wireless bridges provide connectivity (backhaul) between disconnectd wired networks
* **Core Role**: The WLAN is the network; suitable for small networks usually, not large networks
* **Wireless Personal Area Network (WPAN)**: wireless communications within small range with limited throughput or small-scale mesh (ZigBee, RFID, Bluetooth)
  * Bluetooth can interfere with Wi-Fi, but this is largely eliminated with adaptive frequency hopping
* **Wireless Metropolitan Area Networks (WMAN)**: typically operated by a service provider who leases services to subscribers (WiMAX, requires licensing)
* **Wireless Wide Area Networks (WWAN)**: wireless wide area networks (network that connect multiple WANs together) (Free Space Optics, microwave)
