Version 2.0 - ISAN + Waypoint + Heading
![Full-System](images/FullSystem.jpg)

## Added support for up to 16 waypoints. Added Heading and Pitch (Thanks LizardFish).  Upgraded ISAN to new version with more reliable speed and other features.

This is the ISAN system from the Collective. 
![Coordinates](images/Coordinates.jpg)

It has been modified to work with my waypoint system and adding in heading and pitch from LizardFish.  The system will store up to 16 waypoints, cycle up and down (wrapping at the ends) and has an overwrite and home feature (goes to wp1).

"Pitch is your "vertical" angle from the Z axis with 0 being flat along the plane of the belt, and -90 and 90 being perpendicular.
Heading is your "horizontal" angle from the Z axis with 0 being along it pointing into the belt, 90 being along the X axis pointing "left" along the belt, and it wrapping back around to 360 pointing back into the belt"

# Getting Started
You can install all or part of this system. These instructions assume you are installing it all. The ISAN.yolol is the same as the one found on their github as of 8/17/21, except it has been modified for Mono mode accuracry (pr=1), speed indication (sp=1),memory chip storage of X, Y and Z, and support of heading and pitch system.

#### Materials List for whole system
* Advanced YOLOL Chip - ISAN.yolol script.
* Advanced YOLOL Chip - DTW.yolol script.
* Basic YOLOL Chip - WPIncrement.yolol script.
* (OPTIONAL) Basic YOLOL Chip - Deltas.yolol, needed if display of current deltas is desired.
* 3 YOLOL Memory Chips - One for storing `X`, `Y`, `Z` and current WP's `wX`, `wY`, `wZ`, and current `wpnum`.  One for storing up to 10 waypoints. One for storing another 6 waypoints and variables needed for heading and pitch
* 4 Warning Buttons - Used for WP Increment, WP Decrement, WP Save, and WP Home Select. - IF YOU USE OTHER BUTTONS, the variable `wpb` must be on some device or memory chip.
* 4 24x24 Text Screens - One for ISAN, one for current deltas (OPTIONAL), one for Waypoint Info, one for heading and pitch
* 1 progress bar (OPTIONAL) - Used to display current WP by the selectors.

#### Setup Instructions - Note: `wpb` is a critical field.  If you do not use warning buttons, you must create this field in memory chip 1.
1. Install all chips for desired level of system.  Be sure to bolt them in where appropriate.  Remember Memory chips only go in one way and can vanish if not inserted properly.  Recommend inserting memory chip, then yaw slightly on ship, see if its still in place.
2. Memory Chip 1.  On the chip, set the following fields: `X`, `Y`, `Z` to 1000, `wx`, `wy`, `wz` to 1000, `wpc` to "1000 1000 1000", `wpnum` to 1.  ![MEMORY-CHIP1](images/MemChip1.jpg)
3. Install the modified ISAN.yolol from here on an Advanced Chip.  Set up the receivers fields and data screen name (`_`) per https://isan.to/isan.pdf. The Waypoint system doesnt care if you are mono or quad mode.  If quad mode, you can set pr=0 in the script to turn off precision.  The isan.yolol in this folder is modified, do not use the vanilla version. (Display and Reciever fields should be updated as shown in the PDF) ![ISAN-SCREEN](images/ISANScreen.jpg)
4. (OPTIONAL) Install Deltas.yolol on basic chip.  On a Text Screen, rename PanelValue field name to `Deltas`.  When moving, this will show your current delta X, Y and Z along with OPENING or CLOSING in reference to X, Y and Z to selected Waypoint.![DELTAS-SCREEN](images/DeltasScreen.jpg)
5. Install Memory Chip 2.  On the chip, set the fields to: `wp1` to `wp10`.  Set the values to "1 1 1" unless you have specific waypoints you want to put in. ![MEMORY-CHIP2](images/MemChip2.jpg)
6. Install Memory Chip 3.  On it set fields `i`, `j`, `k`, `l` to 0, set fields `wp11` to `wp16` to "1 1 1". ![MEMORY-CHIP3](images/MemChip3.jpg)
7. Install DTW.yolol on an advanced chip.  On a text screen, rename PanelValue field name to `DTW`.  This will display Waypoint Number, Distance, and delta X, Y, Z to it. ![DTW-SCREEN](images/DTWScreen.jpg)  On another text screen, renamed PanelValuye field to `Heading`  ![HEADING](images/Heading.jpg)
8. Install WPIncrement.yolol on an basic chip. Install 4 warning buttons. Rename ButtonState field names to `wpi`, `wpd`, `wps`, `wph`.  (Increment, Decrement, Save, Home).  Rename all ButtonEnableBlink fields to `wpb`.  ButtonStyle should be 1.  ButtonColor is user preference, I use Red(0) for decrement, Green(2) for increment, Blue(3) for Save, and Orange(1) for Home. ![WP-Buttons](images/WPInc-DecButtons.jpg)  Note: `wpb` is a critical field.  If you do not use warning buttons, you must create this field in memory chip 1.
9. (OPTIONAL) Install progress bar near warning buttons if needed to show currently selected waypoint. Name PanelValue to `wpnum`.  Minvalue 0, maxvalue 16.

#### Usage Instructions - Note, if DTW.yolol is stuck on line 3, change the goto at the end to goto1 then back to goto3+c<0
1. During normal flight, the ISAN screen will show you current X, Y and Z and Speed.  The Deltas screen will show you your current X, Y and Z deltas based on current flight direction and speed along with OPENING or CLOSING re XYZ of waypoint. The DTW screen will show currently selected waypoint, distance to it, and delta X, Y and Z to it.  The Heading screen will show heading and pitch stably AFTER flying in a straight line for a few moments.  Do not use this for precision flying.
2. To fly to your waypoint, if DTW says you are -500X you would want to fly plus X, etc.  Also if all 3 fields say CLOSING you are going in right general direction, but note the magnitudes of the deltas.
##### IMPORTANT: When using the Waypoint buttons, press them one time, wait for blinking to stop before pressing another.  DTW display will show PARSING WAYPIONT while its changing over.
3. To raise or lower current waypoint, press the Increment or Decrement warning button.  It wraps from 10 to 1 and 1 to 10.  Wait for blinking to stop and it's set.
4. To overwrite current waypoint, press the Save warning button.  You will get the same blinking and PARSING message.
5. To go to waypoint 1 press the Home warning button. (Saves time if you are on 5 for example).  Waypoint 1 is always considered home.

IF SOMETHING ISN'T WORKING - Recommend putting chips on a socket or chip reader insert so you can watch them run live and see where they are getting stuck.
