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
  card:
    title: Eating power
```

Automatically group all kitchen entities:
```yaml
- type: entity-filter
  filter:
    - entity_id: '*kitchen*'
  card:
    title: Kitchen
```

Show only people that are at home using 'glance':
```yaml
- type: entity-filter
  filter:
    - domain: device_tracker
      state: 'home'
  card: 
    type: glance
    title: People at home
```

![entity-filter](https://user-images.githubusercontent.com/7738048/41775896-71d42556-762e-11e8-8b02-d75c7824300a.png)


### Feedback
- Support exceptions (blacklist not just whitelist). Example: show this pattern but except this pattern [#41](https://github.com/home-assistant/ui-schema/issues/41)
- Support ordering [#47](https://github.com/home-assistant/ui-schema/issues/47)
- Option to hide when empty [#48](https://github.com/home-assistant/ui-schema/issues/48)