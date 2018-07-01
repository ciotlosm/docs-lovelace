### Plant status
A card for all the lovely botanists out there.

![plant-status](https://user-images.githubusercontent.com/7738048/41775904-72f95ae6-762e-11e8-9c0c-c22aa76cb082.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `plant-status`
| entity | string | **Required** | Entity id of `plant` domain

**Example**

```yaml
- type: plant-status
  entity: plant.bonsai
```