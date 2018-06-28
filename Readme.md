# Lovelace UI 

<img align="right" height="250px" src="https://user-images.githubusercontent.com/7738048/41777567-6f8caa1a-7634-11e8-8ff4-a0589240d724.png">

Lovelace is an **experimental** UI for [Home Assistant](https://www.home-assistant.io/) added in 0.72.0. This is *NOT* the official documentation but a walkthrough of the current cards & features.

For the official and more technical documentation please use [developer docs for Lovelace](https://developers.home-assistant.io/docs/en/lovelace_index.html)

> To reports bugs or raise feature requests, please use https://github.com/home-assistant/ui-schema/issues

> To access **lovelace** please go to `dev-info` and click the link **Try out the new Lovelace UI (experimental)** or [this method](https://github.com/ciotlosm/docs-lovelace#use-lovelace-default-view)

## Cards
Cards are the smallest unit of organisation, and provide a great setup to group functionality. 

- [camera-preview](card-camera-preview.md)
- [entities](card-entities.md)
- [entity-filter](card-entity-filter.md)
- [entity-picture](card-entity-picture.md)
- [glance](card-glance.md)
- [history-graph](card-history-graph.md)
- [iframe](card-iframe.md)
- [markdown](card-markdown.md)
- [media-control](card-media-control.md)
- [picture-glance](card-picture-glance.md)
- [plant-status](card-plant-status.md)
- [weather-forecast](card-weather-forecast.md)
- [picture-elements](card-picture-elements.md)

You can also have custom cards now. The way to add custom cards is [really easy](https://developers.home-assistant.io/docs/en/lovelace_custom_card.html)!

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

## Migration script
Thanks to [@OttoWinter](https://github.com/OttoWinter) for the [migration script](https://gist.github.com/OttoWinter/730383148041824bc47786ea292572f8) from the old interface.


## Use lovelace (Default view)

To make the Lovelace UI the default dashboard view use the setup described below. 

### New to lovelace

> This will change in 0.73.0 - Make sure to visit again

1. Create a new file under your `config/www` folder and name it `lovelace.html`

Content of `lovelace.html`

```html
<script>
    if (window.location.pathname === "/states") {
        window.location.href = "/lovelace"
    }
    window.addEventListener("location-changed", function (e) {
        if (e.currentTarget.location.pathname === "/states") {
            window.location.href = "/lovelace"
        }
    });
</script>
```

Information on path for `lovelace.html` (Hass.io example):

```bash
core-ssh:/config/www# pwd
/config/www
core-ssh:/config/www# ls 
lovelace.html
```

2. Tell Home Assistant to load this file by referencing it inside your `configuration.yaml`

Example configuration:

```yaml
frontend:
  javascript_version: latest
  extra_html_url:
    - /local/lovelace.html
```

> If you don't use `javascript_latest` just make sure you use the correct setup as in the [documentation](https://www.home-assistant.io/components/frontend/#configuration-variables)

3. Restart your Home Assistant and force a clear cache on your browser and a few force reloads on IOS app

### Manual javascript

TBC: Coming in 0.73.0

### Changes to hack (users already on lovelace)

TBC: Coming in 0.73.0

## Templating
Templating cards is really easy now with custom cards. See the example in the [docs](https://developers.home-assistant.io/docs/en/lovelace_custom_card.html#defining-your-card). I recommend trying it out just to see how simple it can be.

## Debugging
As entities no longer show up automatically on your interface, it is recommended that you get a View to show everything you have available to configure inside cards on your interface and other views. For this, the entity-filter card is the best to use. You can find below a configuration that does this for you. 

```yaml
- tab_icon: mdi:settings
  name: Debugging
  cards:
    - type: entity-filter
      filter: [{}]
      card_config:
        title: All entities
```

## Example
To get you started you can use the `demo` platfrom in your [configuration.yaml](configuration.yaml) and try out the included [sample file](ui-lovelace.yaml)
