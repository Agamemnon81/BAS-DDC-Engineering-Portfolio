# Logic Design Rationale

## Delay on Make
Prevents nuisance starts and short cycling.

## Fan Proof Alarm
Protects against unnoticed fan failure and potential coil freeze.

## Mixed Air Target (55°F)
Industry standard balance between economizer benefit and coil protection.

## Freeze Latching Strategy
Prevents automatic restart after freeze event.

## BACnet Object Design

- Supply Fan Command → Commandable Binary Output
- Mixed Air Setpoint → Writable Analog Value
- Alarms → Binary Value with priority handling
- Runtime → Analog Value updated periodically

Priority Levels:
- 8 → Normal Control
- 5 → Safety Override
- 1 → Emergency Shutdown
