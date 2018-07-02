### Vertical stack

Stack card will allow you to stack together multiple cards so they always sit together in the same column one on top of the other

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `vertical-stack`
| cards | list | **Required** | List of cards

**Example**

Basic example
```yaml
- type: vertical-stack
  cards:
    - type: camera-preview
      entity: camera.front_door
    - type: entities
      title: Motion Front Door
      entities:
        - binary_sensor.motion_front_door
    - type: camera-preview
      entity: camera.kitchen
    - type: entities
      title: Motion Kitchen
      entities:
        - binary_sensor.motion_kitchen
```

![vertical-stack](https://user-images.githubusercontent.com/32000001/42162436-9c3a8658-7df6-11e8-80ed-3baefad1bcda.jpg)
