# HDD¢ — Poor Man's HDD Clicker

![HDD¢ — Poor Man's HDD Clicker](/assets/images/hddc_github-readme_cover-01.jpg)

Reproduce hard drive activity noise based on activity of an HDD LED header on the motherboard.

Perfect for retro enthusiasts who build their rig with convenience of a flash storage but miss sounds of an actual hard disk drive.

Cheap and easy way. No soldering (unless you want to), no microcontrollers, no nonsense.

This repository explores different implementation options for the device that can be built on the breadboard using inexpensive off-the-shelf components readily available from retailers.

* [**MARK-00**](#mark-00)  
Connect piezo buzzer to HDD activity LED output of motherboard directly. The simplest but quietest option.
* [**MARK-01**](#mark-01)  
Power piezo buzzer with +5V from PSU via NPN transistor. Significantly louder option.
* [**MARK-02**](#mark-02)  
Power piezo buzzer with +5V from PSU via optocoupler. Similar to previous option but with galvanic isolation from motherboard HDD LED output.
* [**MARK-03** (Breadboard)](#mark-03-breadboard)  
Add multivibrator IC to adjust duration of pulses sent to piezo buzzer. Features more "clicky" and adjustable sound.
* [**MARK-03** (PCB)](#mark-03-pcb)  
PCB version of previous option.

Showcase of different versions available on [YouTube](https://youtu.be/AeMDvgbilyM).

MARK-00
-------
![HDD¢ — MARK-00](/assets/images/hddc_github-readme_mark-00_photo-01.jpg)

The simplest (but also the quietest) version, that requires direct connection of piezo buzzer to the HDD activity LED output of motherboard.

Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=6s) (timestamp: 00:06).

<details>
<summary>Click here to view details</summary>

### Breadboard
![HDD¢ — MARK-00 Breadboard](/assets/images/hddc_github-readme_mark-00_bb-01.jpg)

### Schematic
![HDD¢ — MARK-00 Schematic](/assets/images/hddc_github-readme_mark-00_schematic-01.jpg)

### Components

| Place          | Component                                    | Links/Notes            |
|----------------|----------------------------------------------|------------------------|
| BZ1            | HPM14A piezo buzzer (or equivalent)          | [Datasheet](/assets/files/HPM14A.pdf) |
| C1             | 100nf ceramic capacitor                      | Optional               |
| J1, J2         | Male pin headers, 1x2                        | Connect J1 (IN) to M/B, J2 (OUT) to chassis LED (if present) |
| -              | SYB-170 mini solderless prototype breadboard |                        |
| -              | Jumper wires                                 |                        |

### Files
* Breadboard: [Fritzing](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-00/fritzing/HDD-Clicker-Mark-00.fzz)
* Schematic: [KiCad](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-00/kicad/HDD-Clicker-Mark-00.zip)
* [Hires exports](/mark-00/export)

</details>

MARK-01
-------
![HDD¢ — MARK-01](/assets/images/hddc_github-readme_mark-01_photo-01.jpg)

A sure way to increase the volume is to power pizeo buzzer separately. We'll connect it to +5V power rail coming from the PSU (usually the red wire of a Molex or FDD power connector). For control, we'll use an NPN transistor connected to the HDD activity LED output of the motherboard.

Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=76s) (timestamp: 01:16).

<details>
<summary>Click here to view details</summary>

### Breadboard
![HDD¢ — MARK-01 Breadboard](/assets/images/hddc_github-readme_mark-01_bb-01.jpg)

### Schematic
![HDD¢ — MARK-01 Schematic](/assets/images/hddc_github-readme_mark-01_schematic-01.jpg)

Notice, that we don't connect our circuit to the GND of the PSU explicitly. That's intentional. Output of the HDD activity LED header is usually driven with some kind of transistor internally, and depending on the motherboard that transistor can be placed either on `-` or `+` line of the connection (completing the circuit once it's active and making LED light up). If it is placed on `-` that will make it normally disconnected from the ground plane - and our hypothetical connection to the GND of the PSU would make it permanently connected making LED always shine (and piezo buzzer silent - since it produces sound only when switching is happening, not when constant power is applied).

### Components

| Place          | Component                                    | Links/Notes            |
|----------------|----------------------------------------------|------------------------|
| BZ1            | HPM14A piezo buzzer (or equivalent)          | [Datasheet](/assets/files/HPM14A.pdf) |
| C1             | 100nf ceramic capacitor                      | Optional               |
| R1             | 15K resistor                                 |                        |
| R2             | 220 resistor                                 |                        |
| D1             | LED                                          | Optional, if not used - place jumper wire in its place |
| Q1             | 2N3904 NPN BJT transistor (or equivalent)    | [Datasheet](/assets/files/2N3904.pdf) |
| J1, J2         | Male pin headers, 1x2                        | Connect J1 (IN) to M/B, J2 (OUT) to chassis LED (if present) |
| J3             | Male pin headers, 1x4                        | Connect to +5V coming from PSU (only one pin of the header is actually connected to +5V) |
| -              | SYB-170 mini solderless prototype breadboard |                        |
| -              | Jumper wires                                 |                        |

### Files
* Breadboard: [Fritzing](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-01/fritzing/HDD-Clicker-Mark-01.fzz)
* Schematic: [KiCad](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-01/kicad/HDD-Clicker-Mark-01.zip)
* [Hires exports](/mark-01/export)

</details>

MARK-02
-------
![HDD¢ — MARK-02](/assets/images/hddc_github-readme_mark-02_photo-01.jpg)

MARK-01 wasn't connected to the GND of the PSU explicitly, so we only used +5V rail (and ground connection came from the `-` of the HDD activity LED header of the motherboard once it's active). A more correct way to implement the buzzer connection to the motherboard is to achieve galvanic isolation (of buzzer circuit from the motherboard). This is usually accomplished using an optocoupler.

Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=144s) (timestamp: 02:24).

<details>
<summary>Click here to view details</summary>

### Breadboard
![HDD¢ — MARK-02 Breadboard](/assets/images/hddc_github-readme_mark-02_bb-01.jpg)

### Schematic
![HDD¢ — MARK-02 Schematic](/assets/images/hddc_github-readme_mark-02_schematic-01.jpg)

### Components

| Place          | Component                                    | Links/Notes            |
|----------------|----------------------------------------------|------------------------|
| BZ1            | HPM14A piezo buzzer (or equivalent)          | [Datasheet](/assets/files/HPM14A.pdf) |
| C1             | 100nf ceramic capacitor                      | Optional               |
| R1, R2         | 220 resistor                                 |                        |
| D1             | LED                                          | Optional, if not used - place jumper wire in its place |
| U1             | 4N35 optocoupler (or equivalent)             | [Datasheet](/assets/files/4N35.pdf) |
| J1, J2         | Male pin headers, 1x2                        | Connect J1 (IN) to M/B, J2 (OUT) to chassis LED (if present) |
| J3             | Male pin headers, 1x4                        | Connect to +5V and GND coming from PSU |
| -              | SYB-170 mini solderless prototype breadboard |                        |
| -              | Jumper wires                                 |                        |

### Files
* Breadboard: [Fritzing](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-02/fritzing/HDD-Clicker-Mark-02.fzz)
* Schematic: [KiCad](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-02/kicad/HDD-Clicker-Mark-02.zip)
* [Hires exports](/mark-02/export)

</details>

MARK-03 (Breadboard)
--------------------
![HDD¢ — MARK-03](/assets/images/hddc_github-readme_mark-03_photo-01.jpg)

During periods of high disk activity (when the hard drive access rate is high, such as when running disk speed tests or loading a video game level), piezo buzzer can produce a fairly high-pitched sound, quite unlike that of a real hard drive. To mitigate this effect and make sound more "clicky" rather than "whiny", we should reduce the frequency of activity signal sent to the piezo. This can be achieved using a monostable multivibrator, an integrated circuit that generates pulses of a desired duration in response to a change in the input signal. This way we can limit the maximum frequency at which the buzzer will sound, while still maintaining the "clicking" sound (and being able to adjust it to some extent to our liking).

Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=214s) (timestamp: 03:34).

<details>
<summary>Click here to view details</summary>

### Breadboard
![HDD¢ — MARK-03 Breadboard](/assets/images/hddc_github-readme_mark-03_bb-01.jpg)

### Schematic
![HDD¢ — MARK-03 Schematic](/assets/images/hddc_github-readme_mark-03_schematic-01.jpg)

Turn POT1 (100K) potentiometer to adjust the pulse duration sent to piezo buzzer. Alternatively, use a fixed-value resistor to achieve desired sound. Start by adding a resistor (or several in series) with a value of approximately 50K. Together with resistor R4 (43K) and capacitor C2 (100nF) they form a circuit that adjusts duration of pulses that multivibrator generates (in response to the signal from HDD activity LED output of the motherboard).

Pulse duration is calculated using the formula:  
```math
t = 2.48 * (POT_1 + R_4) * C_2
```

In the case of setting POT1 to 50K we get:
```math
t = 2.48 * (50K + 43K) * 100nF = 2.48 * 93 * 10^3 * 10^{-7} = 0.023s = 23ms
```

This means that there will be an interval of at least 23ms between successive "clicks" emitted by the piezo buzzer (that is, the click frequency will not exceed ~43Hz).

Watch this [video segment](https://www.youtube.com/watch?v=AeMDvgbilyM&t=283s) (timestamp: 04:43), which demonstrates the difference in sound at different values of the POT1 potentiometer.

To learn more about CD4047 and its operating modes, check out this [article](https://circuitdigest.com/tutorial/cd4047-multifunctional-multivibrator-ic-circuit-simulation-working-modes).

### Components

| Place          | Component                                    | Links/Notes            |
|----------------|----------------------------------------------|------------------------|
| BZ1            | HPM14A piezo buzzer (or equivalent)          | [Datasheet](/assets/files/HPM14A.pdf) |
| C1             | 100nf ceramic capacitor                      | Optional               |
| C2             | 100nf ceramic capacitor                      |                        |
| R1, R2         | 220 resistor                                 |                        |
| R3             | 10K resistor                                 |                        |
| R4             | 43K resistor                                 |                        |
| POT1           | 100K potentiometer (3296W-1-104 or equivalent) | [Datasheet](/assets/files/3296W.pdf), use to adjust sound |
| D1             | LED                                          | Optional, if not used - place jumper wire in its place |
| U1             | 4N35 optocoupler (or equivalent)             | [Datasheet](/assets/files/4N35.pdf) |
| U2             | CD4047 multivibrator                         | [Datasheet](/assets/files/CD4047B.pdf), [Overview](https://components101.com/ics/cd4047-multivibrator-ic-pinout-datasheet-circuit-specification), [Usage tips](https://circuitdigest.com/tutorial/cd4047-multifunctional-multivibrator-ic-circuit-simulation-working-modes) |
| J1, J2         | Male pin headers, 1x2                        | Connect J1 (IN) to M/B, J2 (OUT) to chassis LED (if present) |
| J3             | Male pin headers, 1x4                        | Connect to +5V and GND coming from PSU |
| JP1            | Male pin headers, 1x2 with Jumper cap        | Optional, can be used as an on/off switch for the clicker (e.g. can be hooked to the Turbo button) |
| -              | Half-size solderless prototype breadboard    |                        |
| -              | Jumper wires                                 |                        |

### Files
* Breadboard: [Fritzing](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-03/fritzing/HDD-Clicker-Mark-03.fzz)
* Schematic: [KiCad](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-03/kicad/HDD-Clicker-Mark-03.zip)
* [Hires exports](/mark-03/export)

</details>

MARK-03 (PCB)
-------------
![HDD¢ — MARK-03 (PCB)](/assets/images/hddc_github-readme_mark-03-pcb_photo-assembled-01.jpg)

PCB version of MARK-03. Fits the same components in a 41.9x41.9mm footprint with mounting holes (on the bottom edge of PCB) aligned with mounting holes of a typical 3.5" drive cage.

Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=308s) (timestamp: 05:08).

Watch this [video segment](https://www.youtube.com/watch?v=AeMDvgbilyM&t=379s) (timestamp: 06:19) to see a demonstration of real-time sound adjustment.

<details>
<summary>Click here to view details</summary>

### PCB
![HDD¢ — MARK-03 PCB Photo](/assets/images/hddc_github-readme_mark-03-pcb_photo-bare-01.jpg)

![HDD¢ — MARK-03 PCB Render](/assets/images/hddc_github-readme_mark-03-pcb_render-bare-01.jpg)

### Enclosure
![HDD¢ — MARK-03 PCB Enclosure](/assets/images/hddc_github-readme_mark-03-pcb_photo-enclosure-01.jpg)

An enclosure to house the PCB is optional. The enclosure pictured is laser-cut from 1.3mm-thick acrylic and is mounted using a set of M2 nylon screws and standoffs of varying lengths.

### Files
* [KiCad](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-03/kicad/HDD-Clicker-Mark-03.zip)
* [GERBER](https://github.com/Spirik/HDDc/raw/refs/heads/master/mark-03/pcb/gerber/hddc_mark-03_rev.1.0.0_gerber.zip) (ZIP-archive)
* [DIY fabrication](/mark-03/pcb/diy) (PDF, SVG, PNG, etc.)
* [Hires renders](/mark-03/pcb/render)
* [Enclosure](/mark-03/pcb/enclosure) (SVG, PNG, etc.)

</details>

Disclaimer and a License
------------------------

Common sense and basic knowledge of electrical engineering are required for safe use of this project. The author assumes no liability for any property damage or injury resulting from unintentional or otherwise improper use or implementation of this project (or any portion thereof).

This project is licensed under the terms of the CERN OHL v2 Permissive license, except for the datasheets of the components used to build this project, which are distributed for reference only and may be subject to different licence terms.

You should have received a copy of the CERN OHL v2 Permissive license along with this project.  If not, see <https://cern-ohl.web.cern.ch/>.
