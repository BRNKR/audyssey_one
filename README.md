# Audyssey One<!-- omit from toc -->

![A1 Evo](imgs/a1_evo.jpeg)

## Current Version: [A1 Evo Nexus](https://brnkr.github.io/audyssey_one/nexus.html)<!-- omit from toc -->

Unlock the ultimate potential of your home theater audio with A1 Evo Nexus, the next evolution in audio optimization for the discerning audiophile. This advanced tool goes beyond traditional Audyssey calibrations, allowing you to use REW measurements for unparalleled precision and higher resolution. With the ability to fine-tune your sound to an extraordinary level of detail, A1 Evo Nexus offers a significant leap in audio performance, catering to those who are in constant pursuit of better sound.

Effortlessly integrate the power of REW into your home audio setup, gaining a competitive edge over standard calibration methods. This next-gen script fully automates the process, providing even greater flexibility and superior results. Elevate your listening experience and redefine your home entertainment with A1 Evo Nexus.

## Content<!-- omit from toc -->

- [Requirements](#requirements)
- [Video Description](#video-description)
- [Tutorial](#tutorial)
  - [Prepare VLC Player](#prepare-vlc-player)
  - [Setting up your hardware for measurements](#setting-up-your-hardware-for-measurements)
  - [Setting up REW](#setting-up-rew)
    - [Connecting calibration microphone](#connecting-calibration-microphone)
      - [MiniDSP Umik-1/2](#minidsp-umik-12)
      - [Audyssey ACM1HB](#audyssey-acm1hb)
    - [Preferences](#preferences)
    - [Measurement settings](#measurement-settings)
    - [Target curve](#target-curve)
  - [Centering the microphone](#centering-the-microphone)
  - [Playing Atmos sweeps](#playing-atmos-sweeps)
  - [Measuring](#measuring)
  - [Averaging Atmos sweeps](#averaging-atmos-sweeps)
  - [Matching measurements with A1 Evo Nexus](#matching-measurements-with-a1-evo-nexus)
  - [Nexus Warnings explained](#nexus-warnings-explained)
- [Tools](#tools)
  - [\>\> A1 Evo Calibration Tool](#-a1-evo-calibration-tool)
- [Disclaimer](#disclaimer)

## Requirements

- Compatible Audyssey-enabled AV receiver with Speaker/Amp Assignment already done.
- Microphone (just one)
  - Audyssey ACM1HB ([calibration file](./Audyssey_ACM1HB_mic_calibration_file.txt) (```right-click``` -> ```save as```))
  - MiniDSP Umik-1 (sold separately)
- MultEQ Editor App ([iOS](https://apps.apple.com/de/app/audyssey-multeq-editor-app/id1210584625)/[Android](https://play.google.com/store/apps/details?id=com.dmholdings.AudysseyMultEq&hl=de&pli=1)) (sold separately)
- [Room EQ Wizard (v5.40 Beta)](https://www.avnirvana.com/threads/rew-api-beta-releases.12981/)
- [VLC Player](https://videolan.org)
- Audio files
  - [Timing reference file](https://brnkr.github.io/audyssey_one/LosslessAtmosREWSweeps/256kMeasurementSweepReferenceFile_0_to_24000_0_dBFS_48k_acoustic_ref_FL.wav)
  - [Atmos sweep files](https://brnkr.github.io/audyssey_one/LosslessAtmosREWSweeps/atmos_sweeps.m3u)

## Video Description

(Click on Images to go to YouTube-Video)

### A1 Evo Nexus home cinema optimization tool<!-- omit from toc -->

| Part I - The Basics                                                                                           | Part II - REW                                                                                              |
| ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| [![A1 Evo Basics](https://img.youtube.com/vi/tNj-nWR-Yyo/0.jpg)](https://www.youtube.com/watch?v=tNj-nWR-Yyo) | [![A1 Evo REW](https://img.youtube.com/vi/JDOaU-1n3ek/0.jpg)](https://www.youtube.com/watch?v=JDOaU-1n3ek) |

## Tutorial

### Prepare VLC Player

1. Open VLC
2. Go to ```Tools->Preferences->Audio```

   | Settings                     | Value                            |
   | ---------------------------- | -------------------------------- |
   | Output                       | Windows Multimedia Device output |
   | HDMI/SPDIF audio passthrough | Enabled                          |
   | Device                       | [YOUR HDMI RECEIVER NAME]        |

3. Load the sweeps files or the m3u.

### Setting up your hardware for measurements

1. Get IP-address of your AV-Receiver.
   1. Open your ```Windows Explorer```.
   2. Go to ```Network``` on the left side.
   3. Right-click on your receiver and click on ```Properties```.
   4. Write down the IP-Address.
2. Open your webbrowser and type in
   - ```http://[IP-Address]/``` __or__
   - ```https://[IP-Address]:10443```
   1. Turn on your receiver in web interface.
   2. Set ```Network->Network Control```

       | Settings        | Value     |
       | --------------- | --------- |
       | Network Control | Always On |

   3. Set ```Network->Settings```

       | Settings | Value |
       | -------- | ----- |
       | DHCP     | On    |

   4. Set ```Audio->Audyssey```

       | Settings               | Value     |
       | ---------------------- | --------- |
       | MultEQ                 | Reference |
       | DynamicEQ              | On        |
       | Reference Level Offset | 0dB       |
       | Dynamic Volume         | Off       |
       | Audyssey LFC           | Off       |

   5. Set ```Audio->Bass```

       | Settings       | Value |
       | -------------- | ----- |
       | Subwoofer mode | LFE   |
       | LPF for LFE    | 120Hz |

   6. Set ```General->ECO```

       | Settings | Value |
       | -------- | ----- |
       | Mode     | Off   |

   7. Start VLC Player and play an Atmos sweep. This will trigger your receiver to display surround parameters in the web interface, which are otherwise unavailable if the receiver’s decoder is not in Atmos mode. Verify that your receiver has changed the settings by reloading the web interface. Ensure you set it while playing an Atmos track.
   8. Set ```Audio->Surround Parameter```

       | Settings              | Value |
       | --------------------- | ----- |
       | Cinema EQ             | Off   |
       | Loudness Management   | Off   |
       | Low Frequency Effects | 0 dB  |

3. Upload REW measurement mode file to receiver.
   1. Calibrate your Setup with ```MultEQ Editor``` app on three positions, if you didnt already do with same Speakers/Amp Assignment.
   2. Send the calibration-file (```.ady```) to your PC.
   3. Go to [>> A1 Evo Calibration Tool](https://brnkr.github.io/audyssey_one)
   4. Click on ```Upload sample calibration``` and select your Audyssey calibration file on your PC from step 2.
   5. Click on ```Create REW measurement mode file (.ady) w/Dynamic EQ ON/OFF```
      - Choose if you want to have Dynamiq EQ On or Off. It is controllable with .ady-file.
   6. Send the measurement mode file to your MultEQ Editor App.
   7. Upload it to your receiver.
4. Microphone and HDMI
   1. Connect your HDMI to your graphics card on your PC and to one of your inputs of your receiver.
   2. Set the receiver input to the one where your HDMI is connected to.
   3. Connect your Audyssey microphone to the mic input of your PC or connect your MiniDSP Umik to a free USB-Port.

### Setting up REW

__Tip__: It's a good idea to save your REW project after each chapter, allowing you to return to an earlier stage of your work without needing to re-measure your system.

#### Connecting calibration microphone

- Microphone tip is looking to the ceiling.
- Microphone is located at the listening position at ear height.

##### MiniDSP Umik-1/2

1. REW automatically detects Umik microphones on startup.
2. Click on ```Yes``` for accepting using it.
3. Click on ```Yes``` for selecting the calibration file.
4. Select the 90deg calibration file provided by MiniDPS based on your serialnumber.

##### Audyssey ACM1HB

1. Go to ```Preferences->Soundcard```

   | Settings     | Value                   |
   | ------------ | ----------------------- |
   | Input Device | EXCL: [YOUR MICROPHONE] |

2. Go to ```Preferences->Cal files```
   1. Select the provided [calibration file](./Audyssey_ACM1HB_mic_calibration_file.txt) from this repo. You see in pink your used microphone on the right.

#### Preferences

1. Go to ```Preferences->View```

   | Settings             | Value |
   | -------------------- | ----- |
   | Use thick traces     | Off   |
   | Maximum Measurements | 500   |

2. Restart REW.
3. Go to ```Preferences->Api```

   | Settings | Value |
   | -------- | ----- |
   | Api      | On    |

4. Go to ```Preferences->Soundcard```

   | Settings     | Value                              |
   | ------------ | ---------------------------------- |
   | Drivers      | Java                               |
   | Ouput device | EXCL: [NAME OF YOUR RECEIVER/HDMI] |
   | Buffer       | 32k                                |
   | Input Device | EXCL: [YOUR MICROPHONE]            |

   __Set Output Channel Mapping...__

   - Mapping is wrong for Windows.
   - We don't use it, because REW cannot generate Atmos sweeps.

   __Levels__
   1. Selecton on drop-down ```Use main speaker test signal to check/set elvels```.
   2. Click on ```Check levels...```.
   3. Click on ```Next```.
   - __Info:__ You see on level meter that we receive some measurement from the microphone. If not, your microphone or output is not working.
5. Go to ```Preferences->Cal file```
   1. Select your appropiate calibration file for your microphone.
   2. No calibration file for your soundcard.

#### Measurement settings

1. Click on ```Measure```.

   | Settings | Value                         |
   | -------- | ----------------------------- |
   | Range    | 0-24000 Hz                    |
   | Level    | 0.00 dBFS                     |
   | Settings | 256k                          |
   | Timing   | Use acoustic timing reference |

2. Click on ```Check levels``` and set up volume on your receiver to your normal hearing volume.

#### Target curve

1. Click on ```EQ```.
2. Click on ```Target Settings```.

   | Settings              | Value                                                                      |
   | --------------------- | -------------------------------------------------------------------------- |
   | Target type           | None                                                                       |
   | House Curve           | [HarmanKardonTargetCurve](PopularTargetCurves/HarmanKardonTargetCurve.txt) |
   | Add room curve        | Off                                                                        |
   | Target Level (db SPL) | 75.0                                                                       |

### Centering the microphone

We will position the microphone at the center between the front left and right speakers. We will then measure a short REW sweep using the right speaker as the timing reference. The first measurement will be with the left speaker, followed by the right speaker. Since the right speaker is the reference, we will measure the distance difference of both speakers to the microphone and adjust the microphone position accordingly.

1. Click on ```Measure```.

   | Settings   | Value                         |
   | ---------- | ----------------------------- |
   | Range      | 10000-24000 Hz                |
   | Level      | 0.00 dBFS                     |
   | Settings   | 64k                           |
   | Timing     | Use acoustic timing reference |
   | Output     | Front-Left Speaker            |
   | Ref output | Front-Right Speaker           |

2. Click on ```Start``` and the measurement begins.
3. Click on ```Measure```.

   | Settings   | Value                         |
   | ---------- | ----------------------------- |
   | Range      | 10000-24000 Hz                |
   | Level      | 0.00 dBFS                     |
   | Settings   | 64k                           |
   | Timing     | Use acoustic timing reference |
   | Output     | Front-Right Speaker           |
   | Ref output | Front-Right Speaker           |

4. Click on ```Start``` and the measurement begins.
5. Click on ```Overlays->Impulse```
   1. Select ```%``` instead of ```dBFS``` in graph.
   2. Zoom in with the ```+``` control
   3. Click ```CTRL + right mouse button``` to measure the distance of the highest peak of the impulse response of measurement 1 (left speaker) to the corresponding same peak of measurement 2 (right speaker).
   4. You can read the distance in meter. Move your microphone to the left or right accordingly.
6. (You can repeat the steps until you find the sweet spot for your microphone.)

### Playing Atmos sweeps

1. Click on ```Measure->From file->Folder symbol```.
   1. Select ```256kMeasurementSweepReferenceFile_0_to_24000_0_dBFS_48k_acoustic_ref_FL.wav```.
2. Check ```capture noise floor```.
3. Check that your ```Input``` calibration file is the selected for your microphone.
4. Click on ```Start```.
5. Wait for progress bar reaching ```Waiting for timing reference...```.
6. Play with VLC Player the Atmos sweep for the specific speaker you want to measure.
7. ```Right-click``` on the Measurement on the left side of REW and name it like listed on Nexus drop-down menu.

- __Result__: You have one measurement for your speaker and named it.

### Measuring

1. Do ["Playing Atmos sweeps"](#playing-atmos-sweeps) for all your speakers.
2. After you measured all your speakers, move your microphone to a new listening position (e.g. 10 cm to the left/right).
3. Repeat step 1 & step 2 for as many positions you like.

- __Result__: You have one named measurement for each speaker position.

### Averaging Atmos sweeps

1. Add a zero as a suffix to the first measurement name (e.g., FR0) to indicate that it is the one we centered in the ["Centering the microphone"](#centering-the-microphone) section and serves as our reference point. Assign sequential numbers to the other measurements for each speaker (the specific numbering doesn’t matter)
2. Select all measurements for one speaker at once. Be sure, that zero-measurement is on top of all of them.
3. ```Right-click on graph``` -> ```Cross corr align```.
4. ```Right-click on graph``` -> ```Vector average```.
5. Rename the new measurement to your speaker name __without__ suffix (e.g. FR).
6. Delete all measurements of that speaker with suffix.

- __Result__: You have a list of cross correlated and vector averaged measurements for all your speakers (FL, C, FR, SR, SL, SW1 ...).

### Matching measurements with A1 Evo Nexus

1. Go to [A1 Evo Nexus](https://brnkr.github.io/audyssey_one/nexus.html)
2. Click on ```Upload sample calibration``` and select your initial Audyssey calibration file on your PC.
3. Start the calibration process by clicking ```Optimize calibration```. The process takes some minutes.
   - Stay in ```SPL & Phase``` view for performance reasons.
   - __*Yellow warnings in the log window cannot be fixed by Nexus. You have to execute the commands by yourself!*__
4. Upload the calibrated ```.ady``` to your receiver with the MultEQ app.

### Nexus Warnings explained

```markdown
Please set 'Subwoofer Mode' to 'LFE + Main', set 'Bass extraction lpf' to 80 Hz in your receiver.
```

- __Explanation__: If your speaker is set to ```Large``` in the ```Speakers -> Speaker Config``` menu and the ```Subwoofer Mode``` is set to ```LFE + Main,``` the crossover frequency in the ```Speakers -> Crossovers``` menu functions as the bass extraction low-pass filter (LPF). The LPF for LFE can be set to either 120 Hz or 250 Hz: 120 Hz if your subwoofer can reach up to 250 Hz, and 250 Hz if it can only reach around 120 Hz.

1. Open your webbrowser and type in
   - ```http://[IP-Address]/``` __or__
   - ```https://[IP-Address]:10443```
2. Turn on your receiver in web interface (if not already on).
3. Set ```Speakers->Bass```

   | Settings       | Value                |
   | -------------- | -------------------- |
   | Subwoofer Mode | LFE + Main           |
   | LPF for LFE    | 120 Hz __or__ 250 Hz |

4. Set ```Speakers->Crossover```

   | Settings | Value           |
   | -------- | --------------- |
   | Front    | 80 Hz (example) |

## Tools

### [>> A1 Evo Calibration Tool](https://brnkr.github.io/audyssey_one/nexus.html)

## Disclaimer

This source code is independently developed and is not affiliated with, nor has it been authorized, sponsored, or otherwise approved by Audyssey Laboratories, Inc. or its partners, including Denon and Marantz. The term 'Audyssey' is used here for descriptive purposes only to indicate the compatibility of this software with products from Denon and Marantz that utilize Audyssey's technology.
