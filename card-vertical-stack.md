### Vertical stack

Stack card will allow you to stack together multiple cards so they always sit together in the same column one on top of the other.  Keep in mind this can be used with any cards, and even used alongside a [horizontal-stack](card-horizontal-stack.md).

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
    - type: media-control
      entity: media_player.lounge_room
    - type: entities
      title: Motion Front Door
      entities:
        - binary_sensor.motion_front_door
    - type: media-control
      entity: media_player.lounge_room
    - type: entities
      title: Motion Kitchen
      entities:
        - binary_sensor.motion_kitchen
```

![vertical-stack](https://user-images.githubusercontent.com/32000001/42162436-9c3a8658-7df6-11e8-80ed-3baefad1bcda.jpg)

Example using both a Vertical and Horizontal Stack Card
```yaml
- type: vertical-stack
  cards:
    - type: picture-entity
      image: https://images.pexels.com/photos/775219/pexels-photo-775219.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
      entity: group.bedroom_lights
    - type: horizontal-stack
      cards:
        - type: picture-entity
          image: https://i.imgur.com/aOZM05k.jpg
          entity: light.jack_bedside_light
        - type: picture-entity
          image: https://i.imgur.com/rD65Htq.jpg
          entity: light.lara_bedside_light
```
![vertical stack 2](https://user-images.githubusercontent.com/32000001/42166447-f6597e9e-7e02-11e8-9446-c485d4269fe3.PNG)

