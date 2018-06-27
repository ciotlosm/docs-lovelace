### [Entities](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#entities)
Entities will be the most common type of card that will also be the most familiar to people using the standard interface. It groups items together very close to how groups used to do.

Example:
```yaml
- type: entities
  title: Entities card sample
  entities:
    - alarm_control_panel.alarm
    - device_tracker.demo_paulus
    - switch.decorative_lights
    - group.all_lights
    - group.all_locks
```

### Feedback
- Support divider line [#43](https://github.com/home-assistant/ui-schema/issues/43)
- Support global control based on an entity [#35](https://github.com/home-assistant/ui-schema/issues/35)