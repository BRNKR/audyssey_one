# Audyssey One

## Release Notes (30/09/2024) - A1 Evo Nexus

### Patch 1.1

- An object/array typo was causing problems with some AV Receivers
- Although did not seem to cause problems with anyone, perfect response data was in string format rather than floats
- If extended EQ frequency was manipulated in the script to above 250Hz, smoothing the measurement  didn't start from the correct frequency
- Fixed trademark flowing over the log container probelm on 1080p screens

## Release Notes (08/08/2024) - A1 Evo Maestro MJ

- Requires REW Beta 48 or above.
- Doubled up search combinations for directional bass to standard bass conversions refining overall bass response for multiple sub setups significantly,
- Further improved time alignment process for speakers and subs,
- Available delay range for subwoofer is now always a single positive value,
- ‘maxMicDistance’ setting and related checks for it were removed,
- Necessary delay required for best alignment will be prompted in the log even when it’s not within Audyssey limits (hence the need for REW Beta 48 or above),
- Decreased default volume levels for surrounds and heights in the Dynamic EQ calibration,
- Added Denon X4800 and X6800 to receiver list where no bass boost will be added with antireference curve however this list is not yet conclusive,
- Added automatic date and time stamping on saved calibration files. Save dialogue box should now show up with all browsers where you can further customize the files including the save location,
- Added fully customizable “per” speaker crossover frequency search range settings for advanced users. Changes can only be done inside the script and you will find usage instructions there. As usual, leaving them at default (empty) is recommended unless you have a very good reason not to:
- Default target curve has been updated (Target Curve MJ). You can find the previous Evo3 target curve in the “Popular target curves” folder.
- Various user interface improvements and bug fixes.
