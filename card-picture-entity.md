### Entity picture

A very useful card for entities that have on/off states. It allows you to generate a very nice looking card with a big touch area, highly recommended for mobile dashboards on small screens.

You can use different image combination to get a more realistic view for images with lights. The image setup also allows enough flexibility to get your garage picture with the door opened and closed.

You can also use `camera` domain entities to use that as image (will replace `camera-preview`).

![entity-picture](https://user-images.githubusercontent.com/7738048/41775897-71fca8a0-762e-11e8-9f14-71473b4db153.gif)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `picture-entity`
| entity | string | **Required** | Entity id to control via picture.
| camera_image | string | Optional | camera domain entity_id 'camera.demo_camera'
| image | string | Optional| URL of an image.
| state_image | object | Optional | See `state_image` object structure.
| name | string | Optional | Custom name for entity 

`state_image` object structure

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| on | string | Optional | URL of an image used for on state.
| off | string | Optional | URL of an image used for off state.
| home | string | Optional | URL of an image used for home state.
| not_home | string | Optional | URL of an image used for not_home state.
| ... | string | Optional | Any state that is supported by the entity works

**Examples**

Basic example:

```yaml
- type: picture-entity
  image: https://images.pexels.com/photos/775219/pexels-photo-775219.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=295&w=490
  entity: light.bed_light
```

![living-lights](https://user-images.githubusercontent.com/7738048/42104959-57111504-7bd7-11e8-94cc-d09871ee4b45.gif)

Example with night/day:

```yaml
- type: picture-entity
  entity: light.bed_light
  image: http://farm7.static.flickr.com/6153/6220100622_88e64ec5d8_b.jpg
  state_image:
    "on": http://farm7.static.flickr.com/6220/6220100616_a877f41a66_b.jpg
  title: Livingroom lights
```

### Feedback
- ~Support different image for on/off allowing people to show pictures of their garage door opened or closed [#51](https://github.com/home-assistant/ui-schema/issues/51)~