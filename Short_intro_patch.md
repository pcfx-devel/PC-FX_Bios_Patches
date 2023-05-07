# Short_intro_patch

Patch for the PC-FX BIOS to shorten/elininate the introduction "splash" screen

## Overview

There are at least two versions of the BIOS; this discussion primarily focuses on
the initial release, which seems to be the more popular one used on emulators.\
(CRC32 = 76FFB97A)

## Theory of Operation

At the start of bootup, there are some system validations and initializations which
take place. But far more of the time is taken up by a startup "splash" screen,
showing the PC-FX logo and playing a musical note.

This takes roughly 10 seconds, and while it's vaguely reassuring when bootup is rare
or occasional, it is downright aggravating when trying to test new code - not just the
sound and graphic, but even the 10 seconds of delay itself.

So, the idea with this patch is to stop the MJPEG data from being fed to the player,
and to avoid playing the ADPCM sound.

## Technical Overview

The intro video is split into 4 sections, which seem as though they could be contiguous.
The first section is at $FFF0D054.

Each section of video starts with a list of individual frame addresses and sizes.

Each frame itself starts with $FF $FF (for a JPG row that includes new quantization-matrices),
and is followed by rows starting with $FF $F8 (for a JPG row that reuses the previous quantization-matrices). 

The 2nd section is at $FFF2EC24, then $FFF33C64, the last is at $FFF3F424 and finishes at $FFF59BE0.\
Then there is free-space from $FFF59BE0-$FFF59FFF.

