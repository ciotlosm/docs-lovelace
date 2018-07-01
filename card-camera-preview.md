### Camera preview
This card will show a camera preview. 

![camera-preview](https://user-images.githubusercontent.com/7738048/41774717-a2797846-7629-11e8-8882-82fe3b1743cf.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `camera-preview`
| entity | string | **Required** | Entity id of `camera` domain

Example:
```yaml
- type: camera-preview
  entity: camera.demo_camera
```