## Changes in 0.73.0b1
- New feature to allow Lovelace to be default for `/`
- [cards] `column` renamed to `vertical-stack`
- [cards] `row` renamed to `horizontal-stack`
- [cards] `picture-elements` new `state-badge` using `ha-state-label-badge`
- [cards] `picture-elements` renamed `state-badge` to `state-icon`
- [cards] `picture-elements` renamed `state-text` to `state-label`
- [cards] `picture-elements` moved/renamed `service.data` to `service_data`
- [cards] `picture-elements` combined `service.domain` and `service.server` into `service`
- [cards] `entities` allow custom title just like `glance`
- [cards] `entity-filter` allow auto-hide if empty using `show_empty: false`
- [cards] `horizontal-stack`/`vertical-stack` fix card size calculation

## Changes in 0.73.0b0
- [views] `name` renamed `title` to match cards setup
- [views] `tab_icon` renamed `icon` for simplicity
- [views] Now views have deep-links: `/lovelace/3` will link to the tab with id `3`
- [cards] New card: `picture-elements`
- [cards] New card: `column`
- [cards] New card: `row`
- [cards] `entity-picture` renamed `picture-entity` to be consistent with `picture-glance`
- [cards] `glance` fix for title
- [cards] `glance` allow custom title inside glance
- [cards] `entity-filter` removed `card_config` and made `card` property an object
- [cards] Introduced new option support: `show_header_toggle` that supports `true`/`false`
