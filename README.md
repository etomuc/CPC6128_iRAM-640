# CPC6128 iRAM/640

The iRAM/640 is an internal RAM expansion for the Amstrad CPC 6128 which upgrades the computer to a total of 640KB - five times the amount of the original 128KB. 

<img src="/pictures/Iram640_builtin.jpg" width="640"/>

Legacy software that supports the DK'Tronics memory standard will be able to access up to 576K of RAM ([the maximum suppored by DK'Tronics](https://www.cpcwiki.eu/index.php/Standard_Memory_Expansions#Standard_128K-512K_Expansions_.28dk.27tronics.2Fdobbertin-style.29)). More recent software, like e.g. SymbOS, with support for the [enhanced Yarek/RAM7 standard](https://www.cpcwiki.eu/index.php/Standard_Memory_Expansions#Extended_1M-4M_Expansions_.28RAM7.2FYarek-style.29) will see the full 640K. 

## Goals

Main goals of this expansions were:
- fits into a standard CPC 6128
	- for the German Schneider CPC models it might be required to remove the metal shield although there have been user reports that the expansion fits even with the metal shield still installed
- requires no internal modifications, especially no additional internal soldering
- DIY friendly
	- all easy-to solder through-hole components
	- no FPGA, CPLDs can be programmed with many cheap EPROM programmers
- cheap - all components should be available for €20 or less
- long-term availability - all components are still manufactured and will probably be available for decades (at least as NOS)

## License

The expansion and all resources are free to use for personal use.

It is released under the CC BY-NC-ND 4.0 license with the following exception: Commercial production and selling is permitted (and encouraged) as long as the final product will be sold for a maximum of USD 35 / €35 / £32 or the equivalent in other currencies (excl. shipping). 
<sub>Considering the cost of the components (especially when bought in quantities) and the time required for the assembly, this should be sufficient for an interesting profit margin while keeping the expansion affordable for the community.</sub> 

## Support

There is no official support. If you have any questions feel free to join the "Technical support - Hardware related" board on the cpcwiki.eu forum.

## Building the expansion

For a full assembly you need 
- basic soldering skills - as long as you can solder normal through hole components reliably, you will be fine.
- an option to program ATF16V8 CPLDs. This can e.g. be done with some cheap and widely available EPROM programmers like the TL866-II or the T48. The required JED files can be found in the Files directory. 

### Disclaimer

> [!CAUTION]
>**USE AT YOUR OWN RISK.**
>
>This is a hobby project, I am a hobbyist and no engineer. There is always the risk that the expansion can cause harm to your CPC. 
>Although I have tested the expansion on several CPCs for many hours there is no guarantee that it will properly work under all circumstances, with all expansions or with all revisions of the CPC 6128. 
>
>**USE AT YOUR OWN RISK.** 

### Bill of Materials

| Part | Quantity |
| --- | --- |
| PCB | x1 |
| ATF16V8 | x2 |
| 74HCT174 or 74LS174 | x1 |
| AS6C4008-55 | x1 |
| Capacitor 100nF 104 2.56mm | x4 |
| Capacitor 22uF - 2.56mm - 5mm height | x1 |
| Resistor 4.7k | x1 |
| IC socket 40pin | x1 |
| Pin Header 1x20 | x2 |
| XH2.54 Pin male right angle - or Pin Header 1x2 (optional) | x1 |

<img src="/pictures/bom.jpg" width="640"/>

> [!IMPORTANT]
> Make sure to buy all ICs in DIP format.

### PCB

Order PCB here: https://www.pcbway.com/project/shareproject/CPC_iRAM640_internal_RAM_expansion_for_the_Amstrad_CPC_6128_5a46d826.html

or use the Gerber files from the files folder to order from your preferred PCB manufacturer. 

### Assembly

Preparations:

1) Some pin headers need to be adjusted slightly as usually one side of the pin headers is too short and the other too long. You can move the plastic bar with e.g. pliers easily. Move them until the plastic bar almost reaches the mid of the pin header. One side should be slightly shorter than the other side. The short side will be the one that is later plugged into the CPU socket on the motherboard. 

2) Program the ATF16V8 CPLDs with your programmer. Make sure to mark each one so you can later identify PAL1 and PAL2.

**Step 1:**

Add the pin headers and the resistor on the bottom side of the PCB. The "disable" connector is optional and only required if you plan to disable the expansion using a switch from outside of the computer. 

<img src="/pictures/assembly1.jpg" width="640"/>

> [!TIP]
> To easily align the pin headers you can insert them into the CPU socket before soldering. This keeps them nicely in place and aligned.

Cut the pins of the pin header on the top of the PCB closely to the PCBs surface.

**Step 2:**

Solder all ICs on top of the PCB. Don't mix up the position of both PAL ICs. 

<img src="/pictures/assembly2.jpg" width="640"/>

**Step 3:**

Solder the IC socket and then the remaining components on top of the PCB. 

<img src="/pictures/assembly3.jpg" width="640"/>

> [!IMPORTANT]
> Due to the tight packing of all components it's easy to accidentally add shorts or create a cold solder joint. Be careful when soldering and better check all connections twice. 

**Step 4:**

Gently remove the CPU from its socket on the CPC motherboard and insert it into the CPU socket on the expansion. Now insert the expansion into the CPU socket on the motherboard.

Turn on the CPC - and enjoy!

> [!NOTE]
> The CPCs boot message is hard coded in ROM so it will continue to show "128K". To test the expansion you can e.g. use the [Amstrad diagnostics](https://github.com/llopis/amstrad-diagnostics).

## Thanks

Special thanks go to
- Bryce - your willingness to share your knowledge with the community was a great help - without it I would have never even considered doing any electronics. I learned so much! 
- Bread80 - without your [documentation of the RAM logic in the CPC](https://bread80.com/2021/06/03/understanding-the-amstrad-cpc-video-ram-and-gate-array-subsystem/), this would not have been possible
- Prodatron - thanks a lot for your support and providing the source code that allowed me to find the RAM banking issue. (And your [SymbOS](http://www.symbos.de/) is the best reason to get 640K anyway)
- Toto - for your encouraging messages and support
