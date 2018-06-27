### [Glance](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#glance)

Glance cards are a very compact. Very useful to group together multiple sensors for a quick and easy to use view. Keep in mind that this can be used together with 'entity-filter' to create dynamic cards.

![glance](https://user-images.githubusercontent.com/7738048/41775898-721f063e-762e-11e8-89bb-27463552416f.png)

Example:
```yaml
- type: glance
  title: Glance card sample
  entities:
    - binary_sensor.movement_backyard
    - light.bed_light
    - binary_sensor.basement_floor_wet
    - sensor.outside_temperature
    - light.ceiling_lights
    - switch.ac
    - lock.kitchen_door
```

### Known issues
- Aspect radio for images [#29](https://github.com/home-assistant/ui-schema/issues/29)
- Title bug [too short in 0.72.0 and overlapping in 0.72.1] [#45](https://github.com/home-assistant/ui-schema/issues/45)

### Feedback
- Support toggling of entities without opening more-info [#49](https://github.com/home-assistant/ui-schema/issues/49)
- Support justify not just align left [#28](https://github.com/home-assistant/ui-schema/issues/28)
- Allow hiding of values and/or title [#33](https://github.com/home-assistant/ui-schema/issues/33)
- Allow adding empty entities to allow for example a row of 5 items, where 2 are on the left and 2 are on the right with gap in middle