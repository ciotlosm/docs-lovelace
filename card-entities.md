### Entities
Entities will be the most common type of card that will also be the most familiar to people using the standard interface. It groups items together very close to how groups used to do.

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `entities`
| entities | list | **Required** | Entity id's or `{'entity': ''entity_id', 'name': 'name'}`
| title | string | Optional | Card title
| show_header_toggle | boolean | true | Button to turn on/off all entities

**Example**

```yaml
- type: entities
  title: Entities card sample
  entities:
    - alarm_control_panel.alarm
    - device_tracker.demo_paulus
    - switch.decorative_lights
    - group.all_lights
    - group.all_locks
    show_header_toggle: true
```

### Feedback
- Support divider line [#43](https://github.com/home-assistant/ui-schema/issues/43)
- ~Support global control based on an entity [#35](https://github.com/home-assistant/ui-schema/issues/35)~