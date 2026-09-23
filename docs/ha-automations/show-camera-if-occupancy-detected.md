# Show a camera when occupancy is detected

Open a camera feed on a TECHO5 device when occupancy is detected.

## What is this automation?

When the backyard occupancy sensor is triggered while the person is home, it opens the backyard
camera on the selected TECHO5 device for 60 seconds.

## What does it do?

The automation follows this sequence:

1. The backyard occupancy sensor detects a person.
2. Home Assistant checks that `person.yannick` is in `zone.home`.
3. The automation asks the Office TECHO5 device to show `camera.backyard`.
4. The camera feed remains visible for 60 seconds.

## Required inputs

The following entities and action need to be available in Home Assistant:

| Input | Type | Purpose | Example |
|---|---|---|---|
| `person.yannick` | Entity | Confirms that the person is home before showing the feed | `person.yannick` |
| `zone.home` | Zone | Defines the location checked by the condition | `zone.home` |
| `binary_sensor.backyard_person_occupancy` | Entity | Triggers the automation when the backyard sensor detects a person | `binary_sensor.backyard_person_occupancy` |
| `esphome.office_home_show_camera` | Action | Shows a camera feed on the Office TECHO5 device | `esphome.office_home_show_camera` |

## Required integrations

List the Home Assistant integrations this automation uses, with links to their documentation
when available.

- **Reolink**: Provides occupancy detection. [Documentation](https://www.home-assistant.io/integrations/reolink)
- **TECHO5**: Provides the `esphome.office_home_show_camera` action used to show the feed.

## Setup

Make sure the Reolink integration is configured and provides the backyard occupancy sensor
and camera entity. The TECHO5 device must also be connected to Home Assistant and expose the
`esphome.office_home_show_camera` action. Replace the entity and action names with the ones
from your own setup.

## Source

```yaml
alias: Show Backyard Camera on Office Echo Show
description: >-
  Show the backyard camera on the Office Echo Show when backyard motion is
  detected.
triggers:
  - trigger: occupancy.detected
    target:
      entity_id: binary_sensor.driveway_person_occupancy
    options:
      behavior: each
      for: '00:00:00'
conditions:
  - condition: zone.in_zone
    target:
      entity_id: person.yannick
    options:
      behavior: any
      for: '00:00:00'
      zone: zone.home
actions:
  - action: esphome.office_home_show_camera
    data:
      entity: camera.backyard
      seconds: 60
mode: single
```

## Notes

You can substitute an equivalent camera integration if it provides the occupancy sensor and
camera entity needed by the automation. This example uses the entities from one current setup;
replace them with the matching entities from your own Home Assistant instance.
