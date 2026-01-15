# HDD¢ — Poor Man's HDD Clicker

![HDD¢ — Poor Man's HDD Clicker](/assets/images/hddc_github-readme_cover-01.jpg)

Reproduce hard drive activity noise based on activity of an HDD LED header on the motherboard.

Perfect for retro enthusiasts who build their rig with convenience of a flash storage but miss sounds of an actual hard disk drive.

Cheap and easy way. No soldering (unless you want to), no microcontrollers, no nonsense.

This repository explores different implementation options for the device that can be built on the breadboard using inexpensive off-the-shelf components readily available from retailers.

* [MARK-00](#mark-00)  
Connect piezo buzzer to HDD activity LED output of motherboard directly. The simplest but quietest option.
* [MARK-01](#mark-01)  
Power piezo buzzer with +5V from PSU via NPN transistor. Significantly louder option.
* [MARK-02](#mark-02)  
Power piezo buzzer with +5V from PSU via optocoupler. Similar to previous option but with galvanic isolation from motherboard HDD LED output.
* [MARK-03 (Breadboard)](#mark-03-breadboard)  
Add multivibrator IC to adjust duration of pulses sent to piezo buzzer. Features more "clicky" and adjustable sound.
* [MARK-03 (PCB)](#mark-03-pcb)  
PCB version of previous option.

Showcase of different versions available on [YouTube](https://youtu.be/AeMDvgbilyM).

MARK-00
-------
![HDD¢ — MARK-00](/assets/images/hddc_github-readme_mark-00_photo-01.jpg)

The simplest (but also the quietest) version, that requires direct connection of piezo buzzer to HDD activity LED output of motherboard.

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
| BZ1            | Piezo buzzer                                 |                        |
| C1             | 100nf ceramic capacitor                      | Optional               |
| J1, J2         | Male pin headers, 1x2       			        | Connect J1 (IN) to M/B, J2 (OUT) to piezo |
| -              | SYB-170 mini solderless prototype breadboard |                        |
| -              | Jumper wires                                 |                        |

### Files
* Breadboard: [Fritzing](/mark-00/fritzing/HDD-Clicker-Mark-00.fzz)
* Schematic: [KiCad](/mark-00/kicad/HDD-Clicker-Mark-00.zip)
* [Hires exports](/mark-00/export)

</details>

MARK-01
-------
Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=76s) (timestamp: 01:16).

MARK-02
-------
Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=144s) (timestamp: 02:24).

MARK-03 (Breadboard)
--------------------
Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=214s) (timestamp: 03:34).

MARK-03 (PCB)
-------------
Watch [Demo on YouTube](https://www.youtube.com/watch?v=AeMDvgbilyM&t=308s) (timestamp: 05:08).

Disclaimer and a License
------------------------

Common sense and basic knowledge of electrical engineering are required for safe use of this project. The author assumes no liability for any property damage or injury resulting from unintentional or otherwise improper use or implementation of this project (or any portion thereof).

This project is licensed under the terms of the CERN OHL v2 Permissive license, except for the datasheets of the components used to build this project, which are distributed for reference only and may be subject to different licence terms.

You should have received a copy of the CERN OHL v2 Permissive license along with this project.  If not, see <https://cern-ohl.web.cern.ch/>.