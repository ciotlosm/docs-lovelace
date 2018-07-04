# Lovelace UI - [0.73.0b6](changelog.md)

> Use [0.72.1 branch](https://github.com/ciotlosm/docs-lovelace/tree/0.72.1) for older docs

Please follow [official docs](https://www.home-assistant.io/lovelace) and [developer docs](https://developers.home-assistant.io/docs/en/lovelace_index.html) for Lovelace UI. 

## Cards
Cards are the smallest unit of organisation, and provide a great setup to group functionality. 

- [entities](card-entities.md)
- [entity-filter](card-entity-filter.md)
- [glance](card-glance.md)
- [history-graph](card-history-graph.md)
- [horizontal-stack](card-horizontal-stack.md)
- [iframe](card-iframe.md)
- [markdown](card-markdown.md)
- [media-control](card-media-control.md)
- [picture](card-picture.md)
- [picture-elements](card-picture-elements.md)
- [picture-entity](card-picture-entity.md)
- [picture-glance](card-picture-glance.md)
- [plant-status](card-plant-status.md)
- [vertical-stack](card-vertical-stack.md)
- [weather-forecast](card-weather-forecast.md)

## Views
These are exactly as before, tab views with icons or text that help you manage large dashboards with many entities. The views have now deep links like `/lovelace/0`. You can also assign your own [custom ids](view-custom-id.md).

- Using custom id in view, for [nicer navigation paths](view-custom-id.md) in URLs
- Using [icons for tabs](view-icon.md) instead of text
- Using a card to [fill a complete view](view-panel.md), just like panels
- Using themes in views

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| title | string | Optional | Text title of the view
| id | string | number | The id to use in URL path of this view
| icon | string | Optional | The material design icon for the view, uses this instead of title
| panel | boolean | false | Marks view as a panel reusing the first card in list

![views](https://user-images.githubusercontent.com/7738048/41777460-0c432b6e-7634-11e8-8738-ca078a552d06.gif)

## Make Lovelace default

To make the Lovelace UI the default dashboard view use one of the methods below.

#### Using UI

Click the `>> Set lovelace as default page page on this device <<` in `dev-info` panel to make Lovelace the default interface when visiting `/`. 

#### Overview binding

This is a **hack** that will bind `/lovelace` to **Overview** option in the menu instead of `/states` using javascript. It will also set default dashboard for `/` using the same mechanic as **Using UI** method. 

1. Create a new file under your `config/www` folder and name it `lovelace.html`

Content of `lovelace.html`

```html
<script>
    var hack_element = document.querySelector('home-assistant').shadowRoot.querySelector('home-assistant-main').shadowRoot.querySelector('ha-sidebar').shadowRoot.querySelector('paper-icon-item[data-panel="states"]');
    if (hack_element) {
        hack_element.setAttribute("data-panel", "lovelace");
        localStorage.defaultPage = 'lovelace';
    }
</script>
```

2. Tell Home Assistant to load this file by referencing it inside your `configuration.yaml`

Example configuration:

```yaml
frontend:
  extra_html_url:
    - /local/lovelace.html
```

3. Restart your Home Assistant and force a clear cache on your browser and a few force reloads on IOS app
4. [Optional] To view the old dashboard just navigate to `/states`

## Debugging
To see what entities you left out, you can now use the menu `Unused entities`.

![unused-entities](https://user-images.githubusercontent.com/7738048/42287697-0f1dfe00-7fc0-11e8-99ee-f5b312767879.png)

## Rebirth of `entity-filter` from 0.72
Due to popular request, a new custom card is now available (["monster card"](https://github.com/ciotlosm/custom-lovelace)) to achieve similar results as the previous `entity-filter`.

```yaml
views:
- icon: mdi:settings
  id: debug
    cards:
      - type: "custom:monster-card"
        title: My lovely card
        card: glance
        filter:
          include:
            - []
          exclude:
            - domain: group
            - domain: zone
```

## Examples
To get you started you can use the `demo` platfrom in your `configuration.yaml` and experiment with the various examples inside card docs.

Other examples:
- [ui-schema](https://github.com/home-assistant/ui-schema/blob/master/dev_repo_test_config) repo used by devs
- [arsaboo](https://github.com/arsaboo/homeassistant-config/blob/master/ui-lovelace.yaml) own setup

## Migration scripts

Thare are two migration scripts:

> The scripts might not be up to date with 0.73.0 on release day. Please be patient.

- Thanks to [@OttoWinter](https://github.com/OttoWinter) for the [migration script](https://gist.github.com/OttoWinter/730383148041824bc47786ea292572f8)
- Thanks to [@dale3h](https://github.com/dale3h) for the [migration script that works also for packages](https://github.com/dale3h/python-lovelace)