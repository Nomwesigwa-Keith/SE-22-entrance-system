# SE-22 Group Contract

Copy topic names and message formats EXACTLY. MQTT is case-sensitive, and a typo
means messages silently never arrive. If anything changes, edit this file and
tell the group.

## Broker
- Address: test.mosquitto.org
- Port: 1883 (no password)
- Fallback if it is down: broker.hivemq.com, port 1883

## Topics

| Topic | Published by | Subscribed by | Message |
|---|---|---|---|
| SE-22/entrance/access | Entrance | anyone | {"tag":"A1B2","dir":"in","granted":true} |
| SE-22/room1/occupancy | Room 1 | Entrance | {"occupied":true} |
| SE-22/room2/occupancy | Room 2 | Entrance | {"occupied":false} |
| SE-22/config/schedule | Entrance | Rooms (optional) | {"start":7,"end":18} |

## Field meanings
- tag: RFID tag ID, text (allowed tags: A1B2, C3D4, E5F6)
- dir: "in" or "out"
- granted: true or false
- occupied: true or false
- start / end: access hours, 0-24

## Rules
- Only the Entrance publishes the schedule. Nobody accepts schedule changes over MQTT.
- Publish room messages only when the state changes.
- Every terminal is its own Wokwi project, built with ESP-IDF.
- Commit to your own folder every day.

## Owners and links

| Person | Name | Folder | Wokwi link |
|---|---|---|---|
| 1 | | entrance/ | |
| 2 | | room1/ and room2/ | |
| 3 | | entrance/ (SD, menu) | |
| 4 | | entrance/ (network) | |
