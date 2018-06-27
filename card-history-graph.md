### [History graph](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#history-graph)

History graph is a basic card, allowing you to display [History Graph](https://www.home-assistant.io/components/history_graph/) entities

![history-graph](https://user-images.githubusercontent.com/7738048/41775899-72444f02-762e-11e8-8ccc-cdaf401bd4ea.png)

Example:
```yaml
- type: history-graph
  entity: history_graph.recent_switches
```