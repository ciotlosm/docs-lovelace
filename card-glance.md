### Glance

Glance cards are a very compact. Very useful to group together multiple sensors for a quick and easy to use view. Keep in mind that this can be used together with [entity-filter](card-entity-filter.md) cards to create dynamic cards.

![glance](https://user-images.githubusercontent.com/7738048/41775898-721f063e-762e-11e8-89bb-27463552416f.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `glance`
| entities | list | **Required** | Entity id's or an `entity` object (see structure below).
| title | string | Optional | Card title

`entity` object type

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| entity | string | **Required** | An entity_id. Example: 'device_tracker.demo_paulus'.
| name | string | **Required** | A new name for the entity_id

**Examples**

Basic example
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

![glance-with-title](https://user-images.githubusercontent.com/7738048/42103958-89dadac8-7bd3-11e8-95a6-7dfe6a0ebd6b.png)

Example with custom name
```yaml
- type: glance
  title: Better names
  entities:
    - entity: binary_sensor.movement_backyard
      name: Movement?
    - light.bed_light
    - binary_sensor.basement_floor_wet
    - sensor.outside_temperature
    - light.ceiling_lights
    - switch.ac
    - lock.kitchen_door
```

### Known issues
- ~Aspect ratio for images [#29](https://github.com/home-assistant/ui-schema/issues/29)~
- ~Name overlapping bug [#45](https://github.com/home-assistant/ui-schema/issues/45)~

### Feedback
- ~Support toggling of entities without opening more-info [#49](https://github.com/home-assistant/ui-schema/issues/49)~
- Support justify not just align left [#28](https://github.com/home-assistant/ui-schema/issues/28)
- Allow hiding of values and/or title [#33](https://github.com/home-assistant/ui-schema/issues/33)
- Allow adding empty entities to allow for example a row of 5 items, where 2 are on the left and 2 are on the right with gap in middle