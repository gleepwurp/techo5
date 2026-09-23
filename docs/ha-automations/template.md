# Automation name

A short description of the automation and the situation it supports.

## What is this automation?

Describe the use case in a sentence or two. Mention which TECHO5 device or Home Assistant
workflow it relates to, if relevant.

## What does it do?

Describe the behavior from the user's perspective. A short step-by-step list can make the
sequence easy to follow:

1. What starts the automation?
2. What conditions are checked?
3. What actions are performed?
4. What result should be expected?

## Required inputs

List the entities, helpers, devices, services, or values that need to exist before this
automation can be used.

| Input | Type | Purpose | Example |
|---|---|---|---|
| `entity_id` | Entity | What this input is used for | `example.entity` |
| `helper` | Helper | What this helper controls | `input_boolean.example` |
| `value` | Setting | Any value that needs to be changed | `example` |

## Required integrations

List the Home Assistant integrations this automation uses, with links to their documentation
when available.

- **Integration name**: What it provides or why it is needed. [Documentation](https://www.home-assistant.io/integrations/)
- **TECHO5**: Any TECHO5-specific setup or action that is required.

## Setup

Describe any changes needed before adding the automation, such as creating helpers, assigning
an entity, or updating a device name.

## Source

```yaml
# Paste the complete Home Assistant automation here.
```

Alternatively, link to the source file:

- [Source file](path/to/source.yaml)

## Notes

Add useful context, limitations, or adaptations that may help someone use this automation in a
different setup.
