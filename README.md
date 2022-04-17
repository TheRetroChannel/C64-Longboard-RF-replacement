# C64-Longboard-RF-replacement
This is a RF modulator replacement for the longboard Commodore 64 variants - these include ASSY# KU-14194HB, 250407, 250425 and 250466 (for ASSY #250469 and Commodore 128 variants see [C128/C64 shortboard RF replacement](INSERT LINK) ). Note ASSY #326298 is not compatible with either of these RF modulator replacements.

# Feature summary
The RF modulator replacement not only provides a better than stock video output but also includes a slew of extra features:
1. Onboard S-Video output (chroma attenuated to 300mVp-p) for direct connection to a modern S-Video capable display or upscaler
2. Signal passthrough to the mainboard AV DIN connector for mono audio, composite and luma/chroma output (for Commodore luma/chroma compatible monitors)
3. Adjustable luma and chroma output [optional]
4. [Hard reset circuit](https://ist.uwaterloo.ca/~schepers/MJK/hard_reset.html) [optional]
5. Composite colour disable [optional]
6. Direct luma/chroma connection from the VIC-II [optional]
7. Direct audio output via 3.5mm TRS connector - this can be wired for a standard single SID (mono) setup or a dual/stereo SID setup*
8. Hard reset button*

"*" The 3.5mm audio output and hard reset button share the same space on the PCB (where the channel selector switch would normally be), as such only one can be installed on the board. Installing the 3.5mm audio out is recommended, the hard reset circuit can still be utilised with a case mounted tactile switch. See Optional Stuff

# Optional stuff
Before ordering components it is important to discuss the optional features and determine which ones you wish to utilise.
* OPT1 Adjustable luma and chroma output: The PCB has space for the installation of either 2 fixed value resistors or 2 variable resistors. The recommended option is to install fixed value resistors (the values in the BoM showed the correct output levels during testing) but if you wish you may install trimpots here and adjust the output levels yourself (an oscilloscope is recommended for this). 
* OPT2 Hard reset circuit and optional reset button: The PCB includes a hard reset circuit (the function of which is explained in the link above). This can be utilised in two ways: 
1. Install a push button switch directly on the RF modulator PCB - this occupies the same space as the 3.5mm audio output so you can only have one or the other (mono audio output will still be available from the C64 mainboard AV DIN connector)
2. Install or utilise an existing reset button (many C64s have been user retrofitted with a case mounted "soft" reset button). The RF modulator PCB has space for two pins headers to be installed and wired to an existing case mounted reset button - just make sure you disconnect the old wiring if you already have a reset button installed!
* OPT3 Composite colour disable: Certain displays (especially LCDs) show a "checkerboard" pattern when connected via s-video to older equipment like the C64/128. This is usually caused by a chroma level above the s-video standard (300mVp-p), or "chroma bleed" where a small amount of the chroma signal is present within the luma signal. As the chorma and luma must be mixed together to provide a colour composite signal, a certain amount of chroma also makes it's way back into the s-video luma only signal. Part of this can be remedied by disabling the composite colour output - the obvious downside is you will have sharp but monochrome composite output but potentially cleaner s-video output. A pin header on the board is used to enable/disable this option.
* OPT4 Direct luma/chroma from the VIC-II: Much like the composite colour issue and checkerboard pattern detailed above, the C64/128 also has very poor separation of chroma and luma signals on the mainboard itself - they run across the board in parallel with each other. So another way to minimise the checkerboard interference is to bypass the luma/chroma signals running across the mainboard and instead run them directly to the RF modulator PCB. Pin headers are used on the RF modulator side and a board such as [Tebl's lumafix](https://github.com/tebl/C64-Lumafix) can be used to isolate the luma/chomra signals from the VIC-II side (it is not required to use the lumafix portion of this board for this purpose).
* OPT5 Direct mono/stereo audio output: Installing a 3.5mm audio socket allows for either mono or stereo audio output. This is especially useful if you only require s-video output as both the s-video and audio connector utilise the exisitng C64/128 case holes where the RF output and channel selector switch would be - in this configuration you do not need to use the mainboard AV DIN connector at all. A pin header is used to connect the stereo (right) channel audio for dual SID configs or a jumper can be bridged to provide dual mono output for standard SID setups.
 
# Gathering components
Use the gerber files from here(INSERT LINK) and upload them to your preferred PCB manufacturer. You should be safe to leave all options as the default ie. 2 layer FR-4, 1.6mm Board thickness, HASL with lead, etc.

The BoM(INSERT LINK) lists all components required to build one board and also includes friendly part names and example part links for ease of ordering. Most are generic components so you can use your preferred parts supplier but pay close attention to the S-Video and 3.5mm audio connector/reset button part numbers. As most PCB manufacturers require a minimum order of 5 PCBs, it is recommended to multiply the quantites on the BoM by 5 - you can give excess ones away or sell them (AT A RESONABLE PRICE).

# Build
Once you have established which optional features you would like and have the required components it's time to build this thing! Most components have their values printed on the PCB itself but you can always refer to the BoM for guidance. I perfer to start by soldering the pin headers that will stick out from the underside of the board (the ones with squares around them on the bottom of the PCB), then flat components on the top side (resistors, diodes) and move to taller ones as you go. Leave the tallest stuff (top side pin headers and AV connector(s)) until last.

# Test
At this point you should have a completely built board so the only thing left to do is test it. But before you stick it in let's make sure you have everything correct.
* Trimpots if installed should be set to their halfway position (see OPT1 above)
* The hard reset circuit can be left disconnected for now, just make sure you have the pin headers installed (see OPT2 above)
* The composite enable header should have a jumper on it if you plan to use composite video (see OPT3 above)
* The EXT L/C jumpers should be bridged unless you have wired luma and chorma directly from the VIC-II (see OPT4 above)
* The stereo/mono jumper should be brided for standard mono setups, or a pin header installed in RIGHT AUDIO IN for stereo setups (see OPT5 above)

Of couse you will need to remove the original RF modulator, there are 2 or 4 tabs that need to be straightened and 6 to 8 grounding posts to be desoldered. You also need to desolder the signal connections to the modulator - be very careful with these as they are easily damaged if not desoldered properly!

Now time to install the replacement. For this I would recommend soldering just the signal connections (2 groups of 4 pins) to begin with. You want to confirm the board is working and aligned properly before soldering the outer ground posts. 

# Finishing up
Once you are satisfied that everything is working correctly, do a test fit with the C64 case to confirm the s-video and 3.5mm audio/reset button are at the correct height. If everything looks good then go ahead and solder the remining posts to the C64 and enjoy!
