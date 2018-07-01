### [Picture elements](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#picture-elements)

Picture elements card is one of the most versatile type of cards. I am almost sure that those that like to customize a lot in their home assistant interface will **love** this card. 

The cards allows you to position icons or text and even services! on an image based on coordinates. Imagine floor plan, imagine picture glance with no restrictions!

You can customize tap action and even icon color.

![floor-plan](https://user-images.githubusercontent.com/7738048/42103244-26bec55a-7bd1-11e8-8bc9-6a130c513f9e.gif)


```yaml
- type: picture-elements
  image: https://static.vecteezy.com/system/resources/previews/000/102/594/large_2x/free-floor-plan-vector.jpg
  elements:
    - type: state-icon
      tap_action: toggle
      entity: light.ceiling_lights
      style:
        top: 47%
        left: 42%
    - type: state-icon
      tap_action: toggle
      entity: light.kitchen_lights
      style:
        top: 30%
        left: 15%
    - type: state-label
      entity: sensor.outside_temperature
      style:
        top: 82%
        left: 79%
    - type: service-button
      title: Turn lights off
      style:
        top: 95%
        left: 60%
      service: light.turn_off
      service_data:
          entity_id: group.all_lights
```