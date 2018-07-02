## Changes in 0.73.0b2 (Soon :alarm_clock)

### Views
- :mega: Added panel mode for a view to use 1st card to fill whole screen

### Cards
- :wrench: Fix wrapping and padding for `service-button` in `picture-elements`
- :mega: `picture-elements` now supports `navigation` type
- :mega: New card: `picture` for navigation
- `entities` and `glance` custom titles now use `name` not `title`

## Changes in 0.73.0b1

### Cards
- `column` renamed to `vertical-stack`
- `row` renamed to `horizontal-stack`
- `picture-elements` new `state-badge` using `ha-state-label-badge`
- `picture-elements` renamed `state-badge` to `state-icon`
- `picture-elements` renamed `state-text` to `state-label`
- `picture-elements` moved/renamed `service.data` to `service_data`
- `picture-elements` combined `service.domain` and `service.server` into `service`
- :mega: `entities` allow custom title just like `glance`
- :mega: `entity-filter` allow auto-hide if empty using `show_empty: false`
- :wrench: Fix card size calculation `horizontal-stack`/`vertical-stack` 

## Changes in 0.73.0b0
- :mega: New feature to allow Lovelace to be default for `/`

### Views
- :mega: Now views have deep-links: `/lovelace/3` will link to the tab with id `3`
- `name` renamed `title` to match cards setup
- `tab_icon` renamed `icon` for simplicity

### Cards
- :mega: New card: `picture-elements`
- :mega: New card: `column`
- :mega: New card: `row`
- :mega: `glance` allow custom title for entities - rename your entity only in this card
- :mega: `entities` toggle button in header can now be hidden using `show_header_toggle: false`
- `entity-picture` renamed `picture-entity` to be consistent with `picture-glance`
- `entity-filter` removed `card_config` and made `card` property an object
- :wrench: Fix use of groups in `picture-entity`
- :wrench: Fix title in `glance` to avoid overlapping

## Changes in 0.72.1

### Cards
- :beetle: Bug introduced in `glance` card - titles now overlap
- :mega: New card: `iframe`

## Changes in 0.72
- Initial release of the Lovelace UI