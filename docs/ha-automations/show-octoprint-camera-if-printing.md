# Show the OctoPrint camera when printing

Open an OctoPrint camera feed on a TECHO5 device when a 3D printer starts printing.

## What is this automation?

This automation shows the OctoPrint camera on the Office TECHO5 device for 30 minutes when
the printer starts printing.

## What does it do?

The automation follows this sequence:

1. The 3D printer starts printing.
2. The automation asks the Office TECHO5 device to show `camera.octoprint_camera`.
3. The camera feed remains visible for 30 minutes.

## Required inputs

The following entities and action need to be available in Home Assistant:

| Input | Type | Purpose | Example |
|---|---|---|---|
| `binary_sensor.octoprint_printing` | Entity | Triggers when the printer starts printing | `binary_sensor.octoprint_printing` |
| `camera.octoprint_camera` | Entity | Provides the printer camera feed | `camera.octoprint_camera` |
| `esphome.office_home_show_camera` | Action | Shows a camera feed on the Office TECHO5 device | `esphome.office_home_show_camera` |

## Required integrations

- **OctoPrint**: Provides the printer state and camera entity. [Documentation](https://www.home-assistant.io/integrations/octoprint)
- **TECHO5**: Provides the `esphome.office_home_show_camera` action used to show the feed.

## Setup

Make sure the OctoPrint integration is configured and provides the printing sensor and camera
entity. The TECHO5 device must also be connected to Home Assistant and expose the
`esphome.office_home_show_camera` action. Replace the entity and action names with the ones
from your own setup.

## Source

```yaml
alias: Show 3D Printer Camera on Office Echo Show
description: Show the 3D printer camera on the Office Echo Show when printing starts.
triggers:
  - trigger: state
    entity_id: binary_sensor.octoprint_printing
    to: 'on'
conditions: []
actions:
  - action: esphome.office_home_show_camera
    data:
      entity: camera.octoprint_camera
      seconds: 1800
mode: single
```

## Notes

The camera is shown for a fixed 30 minutes after printing starts; it is not automatically
hidden when the print finishes. With `mode: single`, another print-start trigger is ignored
while the 30-minute action is still running.

The entity and action names in this example come from one setup. Replace them with the matching
entities and action from your own Home Assistant instance.

