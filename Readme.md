<img align="right" height="250px" src="https://user-images.githubusercontent.com/7738048/41777567-6f8caa1a-7634-11e8-8ff4-a0589240d724.png">

Version: 0.72.0
> Note that this UI is still Experimental

Migration script availabe
> Thanks to @OttoWinter_ for the [migration script](https://gist.github.com/OttoWinter/730383148041824bc47786ea292572f8)

# Lovelace UI 

Below you will find different types of cards available in the new **Lovelace UI** for [Home Assistant](https://www.home-assistant.io/).

For more in depth documentation on entities, please visit the [developer documentation for Lovelace UI](https://developers.home-assistant.io/docs/en/lovelace_index.html)

The UI is structured in views and a view contains cards as seen on the example in the developer documentation.

> To access **lovelace** please go to `dev-info` and click the link '**Try out the new Lovelace UI (experimental)**' or use the "hack" documented in [make-lovelace-default-hack.md](https://gist.github.com/ciotlosm/9508388876edf92c4c1f3579e740fbd5#file-make-lovelace-default-hack-md) in this gist.

## Views

These are exactly as before, tab views with icons or text that help you manage large dashboards with many entities. 

![views](https://user-images.githubusercontent.com/7738048/41777460-0c432b6e-7634-11e8-8738-ca078a552d06.gif)

Examples:

Without icon:
```yaml
views:
- name: Home
```

With icon and hover text:
```yaml
views:
- tab_icon: mdi:settings
  name: Debugging
```

> Theme is currently not working

## Cards
Cards are the smallest unit of organisation, and provide a great setup to group functionality. 

### [Camera preview](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#camera-preview)
This card will show a camera preview. 

![camera-preview](https://user-images.githubusercontent.com/7738048/41774717-a2797846-7629-11e8-8882-82fe3b1743cf.png)

Example:
```yaml
- type: camera-preview
  entity: camera.demo_camera
```

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

### [Entity filter](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#entity-filter)

Entity filter is a magical type of card. Because it's dynamic if you're smart about it, you can have one card that adapts and that you don't need to touch when adding new entities & sensors to your setup. 

This type of card can also be used together with rest of cards that allow multiple entities, allowing you to use 'glance' or 'picture-glance'. By default it uses 'entities' card model.

![entity-filter-entity](https://user-images.githubusercontent.com/7738048/41776696-686e976e-7631-11e8-95bb-bb69a9494c7d.png)

Examples:

Show only active switches or lights in the house
```yaml
- type: entity-filter
  filter:
    - domain: light
      state: 'on'
    - domain: switch
      state: 'on'
  card_config:
    title: Eating power
```

Automatically group all kitchen entities:
```yaml
- type: entity-filter
  filter:
    - entity_id: '*kitchen*'
  card_config:
    title: Kitchen
```

Show only people that are at home using 'glance':
```yaml
- type: entity-filter
  filter:
    - domain: device_tracker
      state: 'home'
  card: glance
  card_config:
    title: People at home
```

![entity-filter](https://user-images.githubusercontent.com/7738048/41775896-71d42556-762e-11e8-8b02-d75c7824300a.png)

### [Entity picture](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#entity-picture)

A very useful card for entities that have on/off states. It allows you to generate a very nice looking card with a big touch area, highly recommended for mobile dashboards on small screens.

![entity-picture](https://user-images.githubusercontent.com/7738048/41775897-71fca8a0-762e-11e8-9f14-71473b4db153.gif)

Example:
```yaml
- type: entity-picture
  image: https://images.pexels.com/photos/775219/pexels-photo-775219.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
  entity: light.bed_light
```

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

### [History graph](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#history-graph)

History graph is a basic card, allowing you to display [History Graph](https://www.home-assistant.io/components/history_graph/) entities

![history-graph](https://user-images.githubusercontent.com/7738048/41775899-72444f02-762e-11e8-8ccc-cdaf401bd4ea.png)

Example:
```yaml
- type: history-graph
  entity: history_graph.recent_switches
```

### [Markdown](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#markdown)
Markdown card is used to render [markdown](http://commonmark.org/help/)

![markdown](https://user-images.githubusercontent.com/7738048/41775900-7269b8c8-762e-11e8-90f9-5634783d283e.png)

Example:
```yaml
- type: markdown
  content: >
    ## Lovelace

    Starting with Home Assistant 0.72, we're experimenting with a new way of defining your interface. We're calling it the **Lovelace UI**.
```

### [Media controller](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#media-controller)

The media controller card is used to display [Media Player](https://www.home-assistant.io/components/#search/media-player) entities on an interface with easy to use controls. 

![media-control](https://user-images.githubusercontent.com/7738048/41775903-72a685aa-762e-11e8-9b9d-1e73cdb004cc.png)

Example:
```yaml
- type: media-control
  entity: media_player.lounge_room
```

### [Plant info](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#plant-info)
A card for all the lovely botanists out there.

![plant-status](https://user-images.githubusercontent.com/7738048/41775904-72f95ae6-762e-11e8-9c0c-c22aa76cb082.png)

Example:
```yaml
- type: plant-status
  entity: plant.bonsai
```

### [Weather forecast](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#weather-forecast)

Weather forecast is a card to display the weather. Very useful to include on interfaces that people display on the wall. 

![weather-forecast](https://user-images.githubusercontent.com/7738048/41775906-731ad130-762e-11e8-854f-d156a0ff56ef.png)

Example:
```yaml
- type: weather-forecast
  entity: weather.demo_weather_north
```

## Debugging
As entities no longer show up automatically on your interface, it is recommended that you get a View to show everything you have available to configure inside cards on your interface and other views. For this, the entity-filter card is the best to use. You can find below a configuration that does this for you. 

```yaml
- tab_icon: mdi:settings
  name: Debugging
  cards:
    - type: entity-filter
      filter: [{}]
      card_config:
        title: All entities
```