# 🧠 Home Assistant Blueprint – ZBMINI Auto-Repair after Zigbee Leave/Rejoin

**Blueprint name:** Zigbee ZBMINI – leave → permit-join → wait rejoin → repair  
**Author:** DI
**Version:** 1.0  
**Tested on:** Home Assistant 2025.10.3 with Zigbee2MQTT 2.6.2

---

## Overview
This blueprint automatically repairs **Sonoff ZBMINI / ZBMINIR2** devices when they leave the Zigbee network.
It re-enables `permit_join`, waits for a rejoin or announce event, then executes a repair sequence:

- Enables **Detach Relay mode**
- Turns the **relay on**
- Sets **Power-On Behaviour = on**
- Pulses the relay off/on
- Sends notifications throughout the process

Perfect for ZBMINIs that control Zigbee lamps via **Detach Relay** mode.

---

## Installation
1. Copy this URL (raw link to the YAML file):
https://raw.githubusercontent.com/ismailovic/ha-blueprint-zbmini-repair/main/blueprints/automation/zigbee/repair_zbmini_on_rejoin.yaml

2. In Home Assistant:
- Go to **Settings → Automations & Scenes → Blueprints → Import Blueprint**
- Paste the URL above
- Click **Preview**, then **Import Blueprint**

3. Create a new automation using the blueprint and fill in:
- IEEE address of your ZBMINI
- Switch entities
- Power-on select entity

## OR
Use this link:
[![Import Blueprint into Home Assistant](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://raw.githubusercontent.com/ismailovic/ha-blueprint-zbmini-repair/main/blueprints/automation/zigbee/repair_zbmini_on_rejoin.yaml)


---

## Inputs
| Input | Description |
|-------|-------------|
| **IEEE** | Device IEEE address (e.g. `0x08b95ffffebacccd`) |
| **Friendly Name** | For notifications |
| **Permit-Join** | Duration (seconds) |
| **Switch Entity** | ZBMINI relay switch |
| **Detach Relay Switch** | Detach relay mode toggle |
| **Power-On Behaviour** | Select entity |
| **Power-On Option** | on/off/toggle/previous |
| **Delay (s)** | Wait before pulsing |
| **Pulse (ms)** | Off time during pulse |

---

## Example
ZBMINI behind a Zigbee lamp with Detach Relay:
- When the switch leaves the Zigbee network, permit_join is opened.
- When it rejoins, its relay and settings are restored automatically.
- The lamp gets power and reconnects to the network — hands-free.

---

## License
MIT License

