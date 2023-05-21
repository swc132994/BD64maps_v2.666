Doom 64 Stereo Project 1.0
----------------------------------------------------------------
This project is to restore the stereo panning of the Doom 64 soundtrack by Aubrey Hodges that was lost on some formats such as for the Doom 64 Remaster midi implementation and tracker format conversion. Note that this music will not be 100% faithful to the N64 however it is pretty close. You may freely use this music for your modding projects.

- Immorpher


Usage
----------------------------------------------------------------
Doom 64 Remaster:
For your convenience the "Doom 64 Remaster WAD" folder contains a WAD you can load into the Doom 64 Remaster, which will turn the Doom 64 soundtrack into stereo. When modding for the Doom 64 Remaster, the files included in the "Stereo MIDI" and "Tracker IT" will both work. However these files should not be used in Doom 64 EX as it will result in stereo that is too wide.

GZDoom:
When modding for GZDoom use the files in the "Tracker MPTM" or "Tracker IT" folders to have stereo Doom 64 music without a large file size (without the soundfont too). The MPTM format allows the interpolation mode to be set, which I chose to be "cubic" and should be slightly closer to the N64 output. 


Methodology
----------------------------------------------------------------
Here is a description of the problem and how it was compensated for. For the PC ports of Doom 64, its stereo information was stored into the soundfont. The DLS format used on the Doom 64 Remaster, cannot store this stereo information. Further its difficult for the tracker format to translate the stereo information into a track. Thus I figured out a way to translate the soundfont stereo information to the midi tracks. This allows the DLS and tracker formats (after conversion) to play the Doom 64 stereo information. Here are the steps.

1) Convert the Doom 64 midis to standard midis using Aria Maestosa. This software is one of the few midi programs I found that can convert the slightly-unusual Doom 64 midi format to a more standard PC format.

2) Parse the individual midi tracks into additional tracks and apply the stereo panning translated from the Doom 64 soundfont. This is done with a custom MATLAB script.

3) Edit and sometimes touch up the midis using Sekaiju. Sometimes the script parses notes into too many tracks (that arent uniquely stereo) so I recombine them. I also use this step to assign unique channels and do adjustments.

4) Adjust the tempo of the midis to prepare for Impulse Tracker format conversion. Here the tempo is lowered and the midi event time is shrunk to compensate. For example if the tempo is lowered from 196 to 120.96, the midi timings need to be shrunk by 63%.

5) Use OpenMPT to convert to tracker formats. Tempo-adjusted midis are loaded into OpenMPT and then the midi channel panning is doubled (to match the tracker specification) and entered manually into the corresponding channels in OpenMPT. 


Links
----------------------------------------------------------------
Aubrey Hodges - https://aubreyhodges.bandcamp.com/
Immorpher - https://twitter.com/immorpher64 / https://immorpher.bandcamp.com/
Aria Maestosa - https://ariamaestosa.github.io/ariamaestosa/docs/index.html
MATLAB MIDI - https://github.com/kts/matlab-midi
Sekaiju - http://openmidiproject.osdn.jp/Sekaiju_en.html
OpenMPT - https://openmpt.org/
Virtual MIDI Synth - https://coolsoft.altervista.org/en/virtualmidisynth
Doom 64 EX - https://doom64ex.wordpress.com/


Special Thanks
----------------------------------------------------------------
Kinsie - For utilizing the tracker format and sharing tips.
Ken Schutte - For pramming the MIDI tools for MATLAB and troubleshooting


Soundfont Stereo Specifications
----------------------------------------------------------------
Here are the stereo specifications as transcribed from the Doom 64 EX soundfont. They were used in the MATLAB script to specify the stereo panning. Each instrument preset is split up into note/key sections where each has a stereo value from -50 (left) to 50 (right).

Preset 0
0-45 -14.8
46-66 -4.6
67-77 27.3
78-88 -15.6
89-127 27.3

Presets 1 - 17
0-20 -50.0
21-40 -27.3
41-50 18.7
51-55 -17.1
56-60 27.3
61-65 -26.5
66-70 27.3
71-80 -26.5
81-90 27.3
91-100 -28.9
101-127 27.3

Preset 18
0-20 -7
21-40 0
41-50 18.7
51-55 -7
56-60 3.9
61-65 -4.6
66-70 10.1
71-80 -7.8
81-90 17.9
91-100 -12.5
101-127 27.3

Presets 19 - 22 (Same as Presets 1 - 17)
0-20 -50.0
21-40 -27.3
41-50 18.7
51-55 -17.1
56-60 27.3
61-65 -26.5
66-70 27.3
71-80 -26.5
81-90 27.3
91-100 -28.9
101-127 27.3

Preset 23
0-20 1.5
21-40 -7.0
41-50 10.1
51-55 18.7
56-60 -7.0
61-65 -20.3
66-70 10.1
71-80 27.3
81-90 -24.2
91-100 10.1
101-127 -15.6

Preset 24
0-20 -15.6
21-40 1.5
41-50 -15.6
51-55 10.1
56-60 -7.0
61-65 2.3
66-70 -21.8
71-80 18.7
81-90 -7.0
91-100 1.5
101-127 27.3

Preset 25
0-20 -12.5
21-40 10.1
41-50 -7.0
51-55 0.7
56-60 18.7
61-65 -13.2
66-70 27.3
71-80 -15.6
81-90 27.3
91-100 -28.9
101-127 27.3

Preset 26 (same as 24)
0-20 -15.6
21-40 1.5
41-50 -15.6
51-55 10.1
56-60 -7.0
61-65 2.3
66-70 -21.8
71-80 18.7
81-90 -7.0
91-100 1.5
101-127 27.3

Preset 27
0-20 -32.8
21-40 -7.0
41-50 10.1
51-55 1.5
56-60 -7.0
61-65 10.1
66-70 -7.0
71-80 18.7
81-90 1.5
91-100 10.1
101-127 27.3

Preset 28
0-45 1.5
46-66 -14.0
67-77 1.5
78-88 -7.0
89-127 1.5

Preset 29
0-20 27.3
21-40 18.7
41-50 -15.6
51-55 10.1
56-60 -14.0
61-65 27.3
66-70 -7.0
71-80 18.7
81-90 -15.6
91-100 18.7
101-127 0.7

Presets 30-35
0-20 26.5
21-40 -15.6
41-50 10.1
51-55 -7.0
56-60 18.7
61-65 -14.8
66-70 10.9
71-80 -8.5
81-90 11.7
91-100 -19.5
101-127 0.7

Preset 36
0-20 -21.0
21-40 7.8
41-50 -8.5
51-55 16.4
56-60 -29.6
61-65 8.5
66-70 -15.6
71-80 1.5
81-90 18.7
91-100 -24.2
101-127 0.7

Presets 37-127
No soundfont specified stereo


Version History
----------------------------------------------------------------
1.0 Initial Release