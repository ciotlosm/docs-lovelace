### History graph

History graph is a basic card, allowing you to display [History Graph](https://www.home-assistant.io/components/history_graph/) entities

![history-graph](https://user-images.githubusercontent.com/7738048/41775899-72444f02-762e-11e8-8ccc-cdaf401bd4ea.png)

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `history-graph`
| entities | list | **Required** | List of entities to graph.
| hours_to_show | integer | 24 | Hours to show
| refresh_interval | integer | 0 | Refresh interval in seconds
| title | string | Optional | `My Graphs`

**Example**

```yaml
- type: history-graph
  title: 'My Graph'
  entities:
    - sensor.outside_temperature
    - media_player.lounge_room
```
