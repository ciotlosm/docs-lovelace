## [not released] Changes in 0.73.0b2

### Cards
- Fix wrapping and padding for `service-button` in `picture-elements` 

## Changes in 0.73.0b1

### Cards
- `column` renamed to `vertical-stack`
- `row` renamed to `horizontal-stack`
- `picture-elements` new `state-badge` using `ha-state-label-badge`
- `picture-elements` renamed `state-badge` to `state-icon`
- `picture-elements` renamed `state-text` to `state-label`
- `picture-elements` moved/renamed `service.data` to `service_data`
- `picture-elements` combined `service.domain` and `service.server` into `service`
- `entities` allow custom title just like `glance`
- `entity-filter` allow auto-hide if empty using `show_empty: false`
- `horizontal-stack`/`vertical-stack` fix card size calculation

## Changes in 0.73.0b0
- New feature to allow Lovelace to be default for `/`

### Views
- `name` renamed `title` to match cards setup
- `tab_icon` renamed `icon` for simplicity
- Now views have deep-links: `/lovelace/3` will link to the tab with id `3`

### Cards
- New card: `picture-elements`
- New card: `column`
- New card: `row`
- `entity-picture` renamed `picture-entity` to be consistent with `picture-glance`
- `glance` fix for title
- `glance` allow custom title inside glance
- `entity-filter` removed `card_config` and made `card` property an object
- `entities` toggle button in header can now be hidden using `show_header_toggle: false`
