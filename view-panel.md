## Panel view

This type of view uses the first card in the `cards` array to expand it to ocuppy the complete view space, similar to panels. One very good practical use will be for floor plan type of cards.

**Example**

```yaml
views:
- icon: mdi:settings
  id: debug
  title: Floorplan
  panel: true
    cards:
      - type: picture-elements
        image: /local/floorplans/main.jpg
        elements:
          - type: state-icon
            tap_action: toggle
            entity: light.ceiling_lights
            style:
              top: 47%
              left: 42%
```