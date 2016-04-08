# idslabel

Note: This is a work in progress.

![IDSLabel](include/screenshot.png)


## requirements

This application depends on FFmpeg, PortAudio and PyAudio.

#### ffmpeg
To install the ffmpeg binary, download from [here](https://www.ffmpeg.org/download.html). OS specific binaries are under the "Get the packages" section. The binary should be put in the same directory as the idslabel.py file.

#### portaudio
To install PortAudio, the easiest way is to use your operating system's package manager.

For OS X, you can use [homebrew](http://brew.sh/):
```bash
$: brew install portaudio
```

For Debian/Ubuntu Linux:
```bash
$: sudo apt-get install portaudio
```

#### pyaudio

The easiest way to install is with pip:
```bash
$: sudo pip install pyaudio
```

## usage

You need to "Load Audio" before "Load Clan". Then, "Load Block", select the clips in the box, and either click "Play Clip" or use the shortcut
(spacebar). After selecting one of the classifications (shortcuts listed below), move on to the next clip with the arrow keys.


There are keyboard shortcuts for selecting the classification and cycling through the clips:

- General Keys
 - shift + a         : load audio file
 - shift + c         : load clan file
 - shift + enter     : load random block
 - shift + \         : load previous block
 - cmd   + s         : save classifications (Mac)
 - ctrl  + s         : save classifications (Linux/Windows)
 - cmd   + shift + s : save as classification (Mac)
 - ctrl  + shift + s : save as classification (Linux/Windows)

- Classification Keys
 - c : CDS
 - a : ADS
 - n : Child Noises
 - m : Multiple Addressee
 - r : Register Switch
 - j : Junk

- Clip Keys
 - up : previous clip
 - down: next clip
 - left          : previous clip
 - right         : next clip
 - space         : play clip
 - shift + space : play whole block



Tiers which are composed of multiple lines, e.g. :
```
*CHN:	0 2662230_2662370
  &=vocalization 2662370_2663380
  0 . 2663380_2663480
```
have a symbol associated with them to signify they're part of the unit ( " ^-- " , it's supposed to be an arrow pointing to the parent tier)

In the classification output, if clips are associated together as part of a multi-line tier, the value in the "multi-tier"
column will be the timestamp of the parent line that they're associated to. In the example provided above, the line with
the timestamp of 2662230_2662370 will be the parent to the following 2 lines.



## status

### implemented

- parsing cha file and extracting Conversation blocks
- chopping up associated audio file
 - each conversation block is chopped as a unit (upon loading)
 - each tier (except comments and *SIL) within a block is chopped into a new audio clip given its timestamp in the cha file
- randomize the blocks and allow the user to load a random one for classification
- list the clips within the currently loaded block, and allow the user to play the audio for a given clip.
- allow the user to select a classification for the currently playing clip
 - cds
 - ads
 - child noises
 - register switch
 - multiple addressee
 - junk
- export classifications to csv
- check github if current IDSLabel is the latest version

### not implemented yet

- connect to server and checkout cha/audio file for labeling
- lots of UI things (make it more convenient)
