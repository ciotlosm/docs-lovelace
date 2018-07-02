### Picture

A very simple card that allows you to set an image to use for navigation to various paths in your interface or to call a service.

![picture-sample](https://user-images.githubusercontent.com/1444314/42169623-44e76f06-7de2-11e8-96ca-9cbefca25df8.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `picture-entity`
| image | string | **Required**| URL of an image.
| navigation_path | string | Optional | Path of URL to navigate to
| service | string | Optional | `light.toggle`
| service_data | object | optional | See service_data object

`service_data` object structure

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| entity_id | string | **Required** | 'light.floor'


**Examples**

Basic navigation example:

```yaml
- type: picture
  image: /local/exit.jpg
  navigation_path: /lovelace/arsaboo
```

> Check the [view](Readme.md#views) setup on how to setup custom ids

Basic navigation example:

```yaml
- type: picture
  image: /local/exit.jpg
  service: light.toggle
  service_data:
    entity_id: light.ceiling_lights
```
