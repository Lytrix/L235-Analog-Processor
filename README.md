# L-235 Analog Processor ##

### Introduction ###
I was interested in the [SR-235](https://www.thinksrs.com/images/instr/boxcar/SR235_FPlg.jpg) as being the equivalent mathematical processor but then in Analog form which I saw in action on Hainbach's channel using this test equipment here: https://www.youtube.com/watch?v=PS_cn9-rgEs 
Also coming from a digital synthesis world using a Kurzweil K2000R Synthesizer years ago which has an awesome VAST engine with mathematical functions called FUN to combine 2 signals and apply mathematical functions on it, I still was searching for an equivalent module in eurorack but did not find any yet.

So I decided to give it a go and build a eurorack DIY version of this module to have these interesting functions available for waveform manipulation in eurorack.

I found the schematics of the SR-235 with courtesy of Stanford Research Systems:
https://www.thinksrs.com/downloads/pdfs/manuals/Boxcarm.pdf


### Main principe ###

The analog processor uses a 4 deck rotary switch to change the algorith and function. This creates different inputs paths to each IC or opamp circuitry to change the way the voltages are handled. One of the IC's is a precision multipier, the AD534. It can be bought second hand for 10 euros, but newer versions go for a whopping 200 euros. Luckily there is a cheaper version available as SMD version (AD633) which is also 10 euros. By adding an extra opamp to the Z input, you basically have the same circuit. 
The A and B inputs are full wave rectified. This is a falstad testing the out the first circuit path: [Full wave rectification test setup](https://tinyurl.com/27wkvqkx)

### Added functionalities ###

#### 1. Attenuverter with -10/+10V Offset 

Attenuverter + Offset with 2x Gain
https://therepaircafe.wordpress.com/2021/04/04/attenuverter-with-gain-and-offset/

https://tinyurl.com/2bdyzzdu
Based on 2 schematics found to build a good setup for input prepping, similar like the awesome [Olivella Modular Signos](https://www.olivellamodular.com/signos.html).

Precision Attenuverter:
https://kassu2000.blogspot.com/2018/04/precision-attenuverter-mixer.html

Added Offset:
https://modwiggler.com/forum/viewtopic.php?t=103687

#### 1b. VCA CV controlled ####
[Moritz Klein Transistor VCA example](https://www.falstad.com/circuit/circuitjs.html?ctz=CQAgjCAMB0l3BWEAmAzNALAdkggnMmAGxFYKSpKkhIao0CmAtGGAFAAu4yAHOBhnBYi-QZHAgm6YWErIE+IpGQY8RMdATIixMBj1xUyLPTBwQAEwYAzAIYBXADYdOKHnz2CV4z1AlToIjxyIh5IMGMcSB0kGC0eUKxkXnxcLCxBM3ErOycXACchEQwPYUkjPyz4NkLvEBKUDHEpZEr4ODYAJRRIPiZ1Hr7WVvFxJu4-Uc02AHdByQHkXvKR2fmWopWoNaW+irqNyC76jwEt33F6JfFYyem5sDKGx5Ew7Yeyt5fuPiO5uoadQivzYthAqFCIAGGAGAzwExYrSq8HBgTAPFYJgxqDw6SS9HQOjCPAyyDwj2iPAQWHA7SOhVQkEEDQhfAaPnaNXBTJAb1ZvNGtOqAHNwZCNvz+mJ3mK+HzIcCZTDMrx6rCxKDwMViFqxjqPK1EUL2lBYPAwLi8LigqgjIlVRzOYUdU1mg1XX5rtUHsVzDq5NtnSIA8RLlo-LbvbrweHQ-UdUcAPI0VWwlRQ6VHbouiougaC8aCqYINbfONlggyiutXbgSv0k6iH5Nx3VZ2q3yK2uOtiirvLLvp0Zc-mK5XNsZRDoM8UVfns+pTo4AD3qkj0tB064wrUEEJAAGUAJIAWQACgAZACiAB0AM4AFU6AEEAHLHg8PxOde8ANQAws+bCriwkDwhC8JMGUqBJGu6b-r+wGSJW5IoEgeDMo0h5HgA4q+z4XveR6vjsyz6CIcbkYG8wWjWZEJsaRyirwpxeO4mzDv84xxkC9ZrIyzJ8ACIJzAJAqbG8RyPIa7rmEwaj1OY4g0hEExFpoIC-gA9s4tjCgwpEeJWvGrIU44DPEGZtB0WkoPQvzcGSNzQHgYSuTiEJgWSdCmualRsEAA)

[electronic druid LM13700 example](https://electricdruid.net/wp-content/uploads/2020/04/EurorackVintageVCA-scaled.jpg)

[DIY VCA with transistors](https://sound-au.com/project213.htm)

Nice payed version: https://modulargrid.net/e/teia-mapvolt

AD633 example
https://modulargrid.net/e/seismic-industries-polarizer

LM13700 example
https://www.haraldswerk.de/VCA/Quad_VCA/Quad_VCA.html

AS3363 example


#### 2. Continuous Argument Filter X with reduced range ####
I reached out to Hainbach who was willing to share some photographs on the internals so I could look for the same brand of components.
I also incorporated his suggestion of changing the filter to a continous potentiometer and limit it to the first 3 steps (0-1M Ohms) to keep it in the audible range.

#### 3. Normalized Patch points before and after each circuit #### 
I wanted to include as many patch points as possible to have a plethora of normalised extra in/outputs on each of the different circuit blocks which are already in the SR-235. Thaty way it can be used as an ARP2600/MS-20 type of pre-routed unit and be able to use a single part of the chain if needed.

#### 4. Bi Polar Half Wave rectification ####
Beside the existing circuits already in the module like full wave rectification, a bi polar half wave option to switch to is also added.
I took inspiration of these nice utility modules where for example the CFM can be utilised to add to separate positive and negative half waves to create new waveshapes easily:
- [Mutable Kinks](https://pichenettes.github.io/mutable-instruments-documentation/modules/kinks/) Signal prep: Invert/Half Wave/Full Wave
- [BiPolar Half Wave Rectifier](http://www.cfmodular.com/BHWR)

To be able to combine new rectified waveshapes I decided to add switches for inversion and positive/negative half wave rectification so the main signal chain can easily be changed.

#### 5. CV control over the selected Argument and Function
A eurorack conversion wouldn't be complete with complete CV control over everything. Therefore I've added CV control to select different circuits via a multiplexer and using a 3-bit Flash ADC to have proper audio rate speed (hopefully!)
- [3-bit Flash ADC test](https://tinyurl.com/2b6dmdgn)

#### 6. CV control over the Argument Filter ####
The Argument Filter is upgraded to a full integrator as was used on the System 700 of Roland.
http://yusynth.net/gear/ROLAND/R700-schematics/707-INSTR-INTERF.pdf

To control the filter a Variable Resistor Ciruit is needed to change the resistance from 0-500k using a BF245 or J112:
https://www.edn.com/a-guide-to-using-fets-for-voltage-controlled-circuits-part-1
and
https://www.ednasia.com/A-guide-to-using-FETs-for-voltage-controlled-circuits--Part-2/ 

https://i.stack.imgur.com/XX1wH.png


#### 7. Additional processing types with AD633 ####


https://www.eddybergman.com/2023/06/AD633ringmodulator.html

http://seismic.industries/wp-content/uploads/2017/08/DIY_Workshop_POLARIZER_Documentation.pdf

1. Frequency Doubler (=Voltage Squarer) (Normalize output A to B to accompish this)
2. Waveshaper (=Voltage Divider A/10*B) W output to negative input opamp to Y1. Output opamp is output. 
4. Square rooter
5. Phase angle detector
6. Rectifier (already have circuits for)
7. VCA 
8. Variable Resistor
10. Ring/AM Modulator (=Multiplier) ([example1](https://musicfromouterspace.com/analogsynth_new/THE_CAVE/Ring%20Mod%20Old%20Design%20I/RingModulator.htm), [example2](https://musicfromouterspace.com/index.php?MAINTAB=SYNTHDIY&VPW=1352&VPH=697))

Great single unit with attenuators:
http://macumbista.net/?p=1314

More in depth:
https://web.archive.org/web/20070123153159/http://www.sowa.synth.net/modular/rm.html
with [schematic](https://web.archive.org/web/20070121113438/http://www.sowa.synth.net/modular/m_rm.gif)
And this example has some GREAT audio examples! Especially the divide creates really nice distortion!:
http://m.bareille.free.fr/modular1/warp633/warp633.htm

And another RM example
https://gitlab.com/rsholmes/ringer

Nice 3hp example:
https://recklessexperimentationaudio.com/products/algebra-lite

Frequency Doubling : Can be done with Waveshaper + gain.

Wavefolder/Ring Mod example:
https://note.com/solder_state/n/n9d138d74b39d

AD633 examples
https://www.youtube.com/watch?v=m6MqNZ7H99w

### Schematic overview of functions with in/outputs ###
![Image](Images/SR-235-Additions.png)