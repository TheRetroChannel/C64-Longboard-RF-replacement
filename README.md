# C64-Longboard-RF-replacement

![Board](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/C64LB%20RF%20FULL.png)

This is a RF modulator replacement for the longboard Commodore 64 variants - these include ASSY# KU-14194HB, 250407, 250425 and 250466 - for ASSY #250469 and Commodore 128 variants see [C128/C64 shortboard RF replacement](https://github.com/TheRetroChannel/C128-C64-Shortboard-RF-replacement). Note ASSY #326298 is not compatible with either of these RF modulator replacements.

I have included as much detail as possible on this page but comparison shots are available [HERE](NEED NEW LINK), and a YouTube build and installtion video is available [HERE](INSERT LINK)

# Feature summary
The RF modulator replacement not only provides a better than stock video output but also includes a slew of extra features:
1. Onboard S-Video output (chroma attenuated to 300mVp-p) for direct connection to a modern S-Video capable display or upscaler
2. Signal passthrough to the mainboard AV DIN connector for mono audio, composite and luma/chroma output (for Commodore luma/chroma compatible monitors)
3. Adjustable luma and chroma output [optional]
4. [Hard reset circuit](https://ist.uwaterloo.ca/~schepers/MJK/hard_reset.html) [optional]
5. Composite colour disable [optional]
6. Adjustable composite mixing [optional]
7. Direct luma/chroma connection from the VIC-II [optional]
8. Direct audio output via 3.5mm TRS connector - this can be wired for a standard single SID (mono) setup or a dual/stereo SID setup*
9. Hard reset button*

"*" The 3.5mm audio output and hard reset button share the same space on the PCB (where the channel selector switch would normally be), as such only one can be installed on the board. Installing the 3.5mm audio out is recommended, the hard reset circuit can still be utilised with a case mounted tactile switch. See Optional Stuff

# Optional stuff
Although everything in the rear half of the board (AV connectors, hard reset circuit, pin headers) can be left unpopulated, it is recommended to install all components now so all features are available should you wish to use them in the future. The pads and through-holes for the RF modulator are easily damaged with multiple removals and reinstallations of RF modulator replacements. Ask me how I know!

Before ordering components it is important to discuss the optional features and determine which ones you wish to utilise.
* OPT1 Adjustable luma and chroma output: The PCB has space for the installation of either 2x 180Ω fixed value resistors (R5 and R7) or 2x 500Ω variable resistors (RV1 and RV2). The recommended option is to install fixed value resistors (the values in the BoM showed the correct output levels during testing) but if you wish you may install trimpots here and adjust the output levels yourself (an oscilloscope is recommended for this). 

![pots vs fixed values](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/pots%20vs%20fixed.png)

* OPT2 Hard reset circuit and optional reset button: The PCB includes a hard reset circuit (the function of which is explained in the link above). Connections must be made to the EXROM (PLA pin 23) and RESET lines (CPU pin 40). This can be utilised in two ways: 
1. Install a push button switch directly on the RF modulator PCB - this occupies the same space as the 3.5mm audio output, so you can only have one or the other (mono audio output will still be available from the C64 mainboard AV DIN connector)

![audio vs reset](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/audio%20vs%20reset%20sw.png)

2. Install or utilise an existing reset button (many C64s have been user retrofitted with a case mounted "soft" reset button). The RF modulator PCB has space for two pins headers (EXTRESET) to be installed and wired to an existing case mounted reset button - just make sure you disconnect the old wiring if you already have a reset button installed!
* OPT3 Composite colour disable: Certain displays (especially LCDs) show a "checkerboard" pattern when connected via s-video to older equipment like the C64. This is usually caused by a chroma level above the s-video standard (300mVp-p), or "chroma bleed" where a small amount of the chroma signal is present within the luma signal. As the chorma and luma must be mixed together to provide a colour composite signal, a certain amount of chroma also makes it's way back into the s-video luma only signal. Part of this can be remedied by disabling the composite colour output before it is mixed with the luma - this may provide a cleaner s-video output but the obvious downside is you will have sharp but monochrome only composite output. A pin header labelled "CVBS ENABLE" on the board is used to enable/disable composite colour mixing. 
 
![cvbs enable](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/cvbs%20en.png)

* OPT4 Adjustable composite mixing: By installing a 120pF variable capacitor (trimmer) at C1, you can adjust how the colour or chorma signal is mixed in with composite video. This adjustment can be made by eye and will vary depending on display. Results will usually range from a smooth/less jagged looking image with colour bleed, to a sharp but jagged image with minimal colour bleed. If composite video is your only option, this should prove to be very useful for you, but as always composite by it's nature is far from perfect. It is recommended to use a ceramic or plastic blade driver when adjusting the trimmer as metal screwdrivers will cause interference, but if a metal driver is all you have at hand just make a small turn, remove the screwdriver, check result, and repeat until you're happy. Remember that a trimmer capacitor only varies over a 360° range - so a full turn is the same as not turning it at all. Alternatively a fixed 100pF ceramic capacitor should yield decent results.

![trimmer vs fixed](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/trimmer%20vs%20fixed.png)

* OPT5 Direct luma/chroma from the VIC-II: Much like the composite colour issue and checkerboard pattern detailed above, the C64 also has very poor separation of chroma and luma signals on the mainboard itself - they run across the board in parallel with each other and alongside a bunch of digital signals. So another way to minimise the checkerboard interference and jailbars is to bypass the luma/chroma signals running across the mainboard and instead run them directly to the RF modulator PCB. There are pin headers labelled EXTERNAL CHR|LUM for connection of these signals on the RF modulator side, and the jumpers on the board next to these connections should be cut to prevent these signals from going back into the C64 mainbaord. You can use 40 pin socket with pins 14 and 15 on the socket bent outwards, then solder wires directly to the bent socket legs - so from the bottom you should have the C64 VIC-II socket, bent pins socket, VIC-II IC. Just remeber to isolate the bent pins from the mainboard socket with a bit of tape. This will also raise the height of the VIC-II, you may be able to fit the lid and heatsink back on (it will be raised at the VIC-II end) or if it no longer fits you should definitely install a [heatsink](https://www.aliexpress.com/item/1005003083684958.html) (INSERT EXAMPLE PIC OF LC BYPASS)

![extLC](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/extlc.png)

* OPT6 Direct mono/stereo audio output: Installing a 3.5mm audio socket allows for either mono or stereo audio output. This is especially useful if you only require s-video output as both the s-video and audio connector utilise the exisitng C64 case holes where the RF output and channel selector switch would be - in this configuration you do not need to use the mainboard AV DIN connector at all. A pin header is used to connect the stereo (right) channel audio for dual SID configs and the associated jumper must be cut separate the left and right channels.

![stereo](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/extaudio.png)
 
# Gathering components
Use the [gerber files](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/tree/main/Gerbers) and upload them to your preferred PCB manufacturer. You should be safe to leave all options as the default ie. 2 layer FR-4, 1.6mm board thickness, HASL with lead, etc. Use the JLC version if ordering through JLCPCB and select "Specify a location" to have them print their order number under the S-Video connector. All other manufacters will likely slap their order number somewhere random on the board unless you pay extra to have them remove it.

The [BoM](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/BOM_C64%20LONGBOARD%20RF%20MOD%20REPLACEMENT.csv) lists all components required to build one board and also includes friendly part names and example part links from AliExpress for ease of ordering. Most are generic components so you can use your preferred parts supplier but the S-Video and 3.5mm audio connector are a very specific type and may be difficult to find outside of AliExpress (I haven't looked elsewhere for these so if you find an exact match elsewhere please let me know). As most PCB manufacturers require a minimum order of 5 PCBs, it is recommended to multiply the quantites on the BoM by 5 - you can give excess ones away or sell them (AT A RESONABLE PRICE). 

# Build
Once you have established which optional features you would like and have the required components it's time to build this thing! Most components have their values printed on the front side of the PCB under the part itself (the text that didn't fit was moved to the back of the PCB) this was done to ease the build process while still giving a "clean" look once the board has been populated. I prefer to start by soldering the flat components (diodes, resistors) and move to taller ones (capacitors, transistors) as you go. Leave the tallest stuff (pin headers and AV connectors) until last.

# Cross-check
At this point you should have a completely built board so the only thing left to do is test it. But before you stick it in let's make sure you have everything correct.
* Trimpots if installed should be set around their halfway position (see OPT1 above)
* The hard reset circuit if installed can be left disconnected for now (see OPT2 above)
* The composite enable header should have a jumper on it if you plan to use composite video (see OPT3 above)

Of couse you will need to remove the original RF modulator, there are 2 or 4 tabs that need to be straightened and 4 to 8 grounding posts to be desoldered. You also need to desolder the signal connections to the modulator - be very careful with these as they are easily damaged if not desoldered properly!

# Install
Insert the RF replacement board into the mainbaord holes for the RF modulator - it should fit without forcing it. If it does not, check the pin headers on the RF replacement to make sure they are straight, and check the RF modulator holes on the C64 to make sure they are completely free from solder. 

Do a test fit with the C64 case to confirm the s-video and 3.5mm audio/reset button are at the correct height and as close to the back of the C64 case as possible - I like to use a bit of blu-tac to hold the RF modulator in place once it's lined up correctly with the case holes, you may need to install the board at a slight angle. Carefully remove the mainboard without bumping the RF modulator out of alignment, then solder the outer mounting posts. At this point the RF modulator shouldn't move and you can remove the blu-tac. Do another test fit to make sure the ports still line up correctly with the case and if so, go ahead and solder the remaining signal posts (2 rows of 4 pins). Connect the optional EXROM and RESET for the HARD RESET circuit, and/or the RIGHT audio input if you plan to use these features.

# Pre-emptive FAQ
Q: Are you going to be selling these?

A: No, I may throw some on eBay but postage would be limited to Australia only as international postage is ridiculously expensive and you could probably order and build 5 of these for less than cost of me sending a single one.

Q: Will these be available as a kit?

A: See above

Q: How long does it take to build and is it difficult?

A: It should take around 30-45 minutes depending on your soldering skills. Everything is through hole so very easy even for a beginner, honestly the most difficult part is removing the original RF modulator - they are a pain in the arse to get out and the pads are easily damaged if you're not careful.

Q: Any plans for a SMD version?

A: Not at this point, for a compact SMD replacement I recommend [c0pperdragon's analog only board](https://github.com/c0pperdragon/C64-Video-Enhancement/tree/master/analog_only). In my testing of various RF replacements I found this one to have great S-Video performance but sub-par composite performance, so it's a neat little board but IMHO it's not good for composite video.

Q: Will there be updates to this project?

A: Very unlikely. Although this is my first time doing PCB design, the project itself has already had numerous changes before being made public (mainly due to me screwing things up, or adding new features). I'm now satisfied that this is the best it's going to get, and no new features or changes should be done.

Q: I've built and installed one of these, but the image still isn't perfect!

A: First of all, that's not a question. Have you tried the optional stuff like disabling composite colour mixing, and the L/C bypass? The VIC-II is doing a lot more than just serving up a video signal, and it's inherently very noisy. The only real options for high quality video are [c0pperdragon's component video board](https://github.com/c0pperdragon/C64-Video-Enhancement), the (sadly) currently inactive [VIC-II Kawari project](http://accentual.com/vicii-kawari/), or emulation! All of which bypass or replace the noisy VIC-II video generation.

Q: I think something is wrong, can you help?

A: Check the [schematic](https://github.com/TheRetroChannel/C64-Longboard-RF-replacement/blob/main/Images/Schematic_C64%20LONGBOARD%20RF%20MOD%20REPLACEMENT.png)

Q: Wow, this is fantastic! How can I ever repay you?

A: It's free, and that's exactly how I wanted it to be. Although it may look simple, the amount of hours I've sunk into this project is ridiculous and that's just how it is with this stuff. I'll be more than happy to see this being shared around and hopefully put to use. If you really want to help me continue doing this kind of thing, consider signing up as a [Patron](https://www.patreon.com/theretrochannel), or you can buy me a [Ko-Fi](https://ko-fi.com/sawickipediatrc)

# To-do
Just a reminder to myself to do the following:
* Finish off the 128/64 shortboard page and insert link
* Film video and insert link here
* Grab some new comparison shots of stock RF vs this one
* Take an actual pic of the LC bypass
