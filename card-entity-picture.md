### [Entity picture](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#entity-picture)

A very useful card for entities that have on/off states. It allows you to generate a very nice looking card with a big touch area, highly recommended for mobile dashboards on small screens.

![entity-picture](https://user-images.githubusercontent.com/7738048/41775897-71fca8a0-762e-11e8-9f14-71473b4db153.gif)

Example:
```yaml
- type: entity-picture
  image: https://images.pexels.com/photos/775219/pexels-photo-775219.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
  entity: light.bed_light
```