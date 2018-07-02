### [Horizontal stack](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#horizontal-stack)

Horizontal stack card will allow you to stack together multiple cards so they always sit next to each other in the space of one column.

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `horizontal-stack`
| cards | list | **Required** | List of cards

**Example**

Basic example
```yaml
- type: horizontal-stack
  cards:
    - type: picture-entity
      image: https://images.pexels.com/photos/775219/pexels-photo-775219.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
      entity: group.bedroom_lights
    - type: picture-entity
      image: https://images.pexels.com/photos/276724/pexels-photo-276724.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=240&w=495
      entity: group.living_room_lights
```

![horizontal stacking](https://user-images.githubusercontent.com/32000001/42163594-22d41fe0-7dfb-11e8-9dbf-a5b6efc09971.PNG)
