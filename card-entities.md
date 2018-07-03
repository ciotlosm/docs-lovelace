### Entities
Entities will be the most common type of card that will also be the most familiar to people using the standard interface. It groups items together very close to how groups used to do.

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `entities`
| entities | list | **Required** | Entity id's or an `entity` object (see structure below).
| title | string | Optional | Card title
| show_header_toggle | boolean | true | Button to turn on/off all entities

`entity` object

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| entity | string | **Required** | An entity_id. Example: 'device_tracker.demo_paulus'.
| name | string | **Required** | A new name for the entity_id

**Example**

```yaml
- type: entities
  title: Entities card sample
  show_header_toggle: true
  entities:
    - alarm_control_panel.alarm
    - device_tracker.demo_paulus
    - switch.decorative_lights
    - group.all_lights
    - group.all_locks
```

### Feedback
- Support divider line [#43](https://github.com/home-assistant/ui-schema/issues/43)
- ~Support global control based on an entity [#35](https://github.com/home-assistant/ui-schema/issues/35)~
