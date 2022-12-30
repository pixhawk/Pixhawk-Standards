# DS-019 Pixhawk standard versions and revisions
## Background
With the introduction of the Pixhawk FMUv5x and FMUv6x standard, versioning of boards and ensuring intercompatibility has become both a major feature as well as a challenge. To comply with the standard, both software maintainers as well as hardware manufacturers must agree to follow the same guidelines. This page is the central place where versions and revisions of Pixhawk FMUs are tracked and managed.

There are two different things to be sensed:

1.  the revision of the FMU board itself. This is called the REVISION (REV).
2.  the version of the base board that carries the FMU. This is called the VERSION (VER).
    

The REV and VER are determined by an ADC which reads a voltage divider. The voltage divider for the VER is on the base board, while the REV is on the FMU.

## EEPROM logic
The goal of the Pixhawk community is to make all base boards and FMUs compatible and interchangeable. Since all hardware manufacturers share this same narrow number space, an additional logic was added.

If the VER resistor encodes the value 0x007, this tells the FMU that it needs to access the EEPROM to poll the true version of the base board. This opens up the number space significantly.

The same logic applies to the REV resistor on the FMU - if it encodes the value 0x007, the true revision of the FMU shall be read from EEPROM.

## Defined versions and revisions

HWTYPE = {v5/6x}{VER}{REV}  

### Base board versions

|     |     |     |
| --- | --- | --- |
| **Value** | **Encoded by** | **Base board VERSION** |
| 0x000 | resistors | Auterion v5x base board |
| 0x001 | resistors | v5x base without px4io |
| 0x002 | resistors | Modal AI |
| 0x003 | resistors | NXP T1 PHY |
| 0x004 | resistors | HB CM4 |
| 0x005 | resistors | HB mini |
| 0x006 | resistors |     |
| 0x007 | resistors | Read Version from EEPROM |
| 0x009 | resistors | Skynode with USB to FMU |
| 0x00a | resistors | Skynode base RC9 & older (no usb) |
| 0x010 | EEPROM | Auterion Skynode RC10, RC11, RC12, RC13 |

### FMU v5x revisions

|     |     |     |
| --- | --- | --- |
| **Value** | **Encoded by** | **FMU v5x REVISION** |
| 0x000 | resistors | FMUv5x RC13 (baro2 on I2C4) |
| 0x001 | resistors | FMUv5x RC15 (baro2 on I2C2) |
| 0x002 | resistors | FMUv5x rev 2 sensor set |
| 0x003 | resistors | FMUv5x rev 3 sensor set |
| 0x004 | resistors |     |
| 0x005 | resistors |     |
| 0x006 | resistors |     |
| 0x007 | resistors | Read Revision from EEPROM |
| 0x009 | resistors |     |
| 0x00a | resistors |     |
| 0x010 | EEPROM |     |

### FMU v6x revisions

|     |     |     |
| --- | --- | --- |
| **Value** | **Encoded by** | **FMU v5x REVISION** |
| 0x000 | resistors |     |
| 0x001 | resistors | CUAV v6x |
| 0x002 | resistors |     |
| 0x003 | resistors | Holybro FMUv6x rev3 |
| 0x004 | resistors | Holybro FMUv6x rev4 |
| 0x005 | resistors |     |
| 0x006 | resistors |     |
| 0x007 | resistors | Read Revision from EEPROM |
| 0x009 | resistors |     |
| 0x00a | resistors |     |
| 0x010 | EEPROM | Auterion FMUv6x 0.6.0  |