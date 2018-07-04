### Custom id

You can now assign a custom id to a view, for nicer navigation paths in URLs. This id allows you to deep-link navigation to this view from cards that allow `navigation_path`. 

**Example**

View:

```yaml
views:
- icon: mdi:settings
  id: debugging
```

Picture card:

```yaml
- type: picture
  image: /local/debug.jpg
  navigation_path: /lovelace/debugging
```