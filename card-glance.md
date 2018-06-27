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