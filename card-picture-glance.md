### [Picture glance](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#picture-glance)

Picture glance is an even more useful type of card that can display sensors, switches, lights and other entities grouped on top of a custom image. Use for this card are for easy recognition inside a large dashboard. What really sets this card apart is the ability to **control** entities directly from the card without the need to open the details of that entity.

> Picture glance supports a display of maximum 10 items (thanks to @jackjohnsonuk)

![picture-glance](https://user-images.githubusercontent.com/7738048/41776092-1194fcc8-762f-11e8-92a7-a40fec0b64a3.gif)

Examples:

```yaml
- type: picture-glance
  image: https://images.pexels.com/photos/276724/pexels-photo-276724.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=240&w=495
  title: Living
  entities:
    - switch.decorative_lights
    - light.ceiling_lights
    - lock.front_door
    - binary_sensor.movement_backyard
    - binary_sensor.basement_floor_wet
```
Picture glance used together with 'entity-filter'
```yaml
- type: entity-filter
  filter:
    - domain: light
  card: picture-glance
  card_config:
    title: Lights
    image: https://images.pexels.com/photos/356048/pexels-photo-356048.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
# credits: @arsaboo
```

### Known issues
- Consistency for entities opening more info dialog [#1339](https://github.com/home-assistant/home-assistant-polymer/pull/1339)

### Feedback
- Support multiple images based on conditions around entities in the card
- Support coordinates for positioning [#52](https://github.com/home-assistant/ui-schema/issues/52)
- Support image source from `camera-preview` or from `media-control` [#39](https://github.com/home-assistant/ui-schema/issues/39)
- Allow local card entity customisation [#36](https://github.com/home-assistant/ui-schema/issues/36)