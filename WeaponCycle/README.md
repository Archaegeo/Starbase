# 3-state Weapon State Machine

## Usage

Cycle through multiple states of your ship weapons with ease. The code assumes you're using at least 2 different weapons that you would like to cycle.

When you press the `:WepSt` simple button, the ship will cycle through the following weapon states:

State | Lasers | Autocannons
--- | --- | ---
0 | ON | OFF
1 | ON | ON
2 | OFF | ON

## Requirements

- Basic YOLOL chip
- Laser Cannons
- Autocannons
- 2 simple buttons (either 12x12 or 12x24 cm)
- 1 warning light button
- 1 text panel

## Setup

- Change field names in devices listed in the [Device Field Names](#device-field-names) section below
- Change field values in devices listed in the [Device Field Values](#device-field-values) section below

### Device Field Names

Variable | Device | Field # | Original Field Name
| --- | --- | --- | --- |
:IsLOn | Laser Cannon Barrel | 1 | MountedWeaponFire
:IsCOn | Autocannon Barrel | 1 | MountedWeaponFire
:CLR | Simple Button 12x12 cm | 1 | ButtonState
:CCF | Simple Button 12x12 cm | 1 | ButtonState
:WepSt | Warning Light Button 12x12 cm | 1 | ButtonState
:WepDisp | Text Panel 24x24 cm | 1 | PanelValue

### Device Field Values

Device | Field Name | Value
--- | --- | ---
Warning Light 12x12 cm | ButtonStyle | 1
