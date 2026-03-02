# AHU Economizer Optimization with Freeze Protection

## System Overview

Single-zone Air Handling Unit including:
- Supply Fan
- Economizer Damper
- Mechanical Cooling
- Freeze Protection
- Smoke Shutdown
- Runtime Tracking

---

## Inputs

- HOA Switch (Binary Input)
- Schedule Status (Binary Value)
- Smoke Detector (Binary Input)
- Freeze Stat (Binary Input)
- Outdoor Air Temperature (Analog Input)
- Return Air Temperature (Analog Input)
- Mixed Air Temperature (Analog Input)
- Fan Status (Binary Input)

---

## Outputs

- Supply Fan Command (Binary Output)
- Damper Position (Analog Output)
- Cooling Enable (Binary Output)
- Alarm (Binary Value)
- Fan Runtime (Analog Value)
- Cooling Runtime (Analog Value)

---

## Fan Start Logic

Fan shall start when:
- HOA = Auto
- Schedule = Occupied
- Smoke = Normal
- Freeze = Normal

Includes:
- 30 second Delay on Make
- 20 second proof verification
- Alarm if proof not proven

---

## Economizer Enable Logic

Economizer enabled when:
- OAT < RAT
- OAT > 45°F
- No freeze condition

Mixed Air Target: 55°F  
Damper controlled via PID loop.

---

## Mechanical Cooling Enable

Cooling enabled when:
- Mixed Air > 58°F
- Damper at 100%
- Supply Fan Running

---

## Freeze Protection

If Mixed Air < 38°F:
- Close damper
- Disable cooling
- Stop fan
- Latch alarm

Manual reset required and MAT > 45°F.

---

## Runtime Tracking

Track:
- Fan runtime hours
- Cooling runtime hours
