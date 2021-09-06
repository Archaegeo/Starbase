# Tadrael's Freighter Escort Fighter

Tadrael's Freighter Escort Fighter has 6 turrets in a unique positioning. There are 3 turrets on the top and 3 turrets on the bottom. The right and left turrets of their respective sides are at a 45 and -45 degree angle respective to the middle turret.

This set of scripts contains two versions: a single chip setup, and a 4-chip + memory chip setup. The single chip setup has a 0.6 second delay because it processes over 3 lines. The second setup has a 0.2 to 0.4 second delay depending on certain race conditions and which chip would process first.

## Setup

- Unbind the `:FCURotationalPitch` and `:FCURotationalYaw` keybinds in your `V` view
- Bind new levers with some `pitch` and `yaw` derivative name instead
- Change the name of `FCURotationalPitch` to the new lever name
- Change the name of `FCURotationalYaw` to the new lever name

### Single Chip Setup

- Copy the `WeaponTracking.yolol` code into a basic YOLOL chip

### Multi Chip Setup

- Copy the following YOLOL files into basic YOLOL chips
  - SetTurretPitchYaw
  - TrigShorthand
  - TopTurrets
  - BottomTurrets
- Configure a memory chip with the fields in the `MemoryChip.yolol` file

## Possible conflict with other YOLOL scripts

The [Multi Chip Setup](#multi-chip-setup) section requires a memory chip that uses short, public variable names that could conflict with the usage of other YOLOL scripts. Take care when using these scripts and rename public fields when appropriate
