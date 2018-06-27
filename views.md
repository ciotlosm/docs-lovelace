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

### Known issues

- Theme is currently only partially usable (font color works)