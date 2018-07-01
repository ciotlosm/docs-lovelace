# Lovelace UI 

<img align="right" height="250px" src="https://user-images.githubusercontent.com/7738048/41777567-6f8caa1a-7634-11e8-8ff4-a0589240d724.png">

Starting with Home Assistant 0.72, we're experimenting with a new way of defining your interface. We're calling it the Lovelace UI.

**Contents**
  * [Overview](#overview)
  * [Cards](#cards)
  * [Views](#views)
  * [Migration scripts](#migration-scripts)
  * [Make Lovelace default](#make-lovelace-default)
      * [Using UI](#using-ui)
      * [Overview binding](#overview-binding)
  * [Templating](#templating)
  * [Debugging](#debugging)
  * [Example](#example)

## Overview
The Lovelace UI is:

 - **Extremely fast**. We create the user interface when the UI configuration changes. When a state changes, we just make the UI represent the current state.
 - **Extremely customizable**. We have a new file for just configuration. In the past, we declined UI specific options because they did not fit in the state machine. They will fit in a configuration file for a user interface.
 - **Extremely extensible**. It's based on the web standard [custom elements](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements). Don't like the built-in cards? Make your own! Custom cards are treated the same as built-in cards and are configured the same way. [Check the docs.](https://developers.home-assistant.io/docs/en/lovelace_custom_card.html)
 - **Making the backend faster**. With Lovelace, the backend will no longer need to maintain entities like groups for the sole purpose of showing them on the frontend.

> This is the very very early version aimed at gathering feedback. Discussion and suggestions are welcome in the [ui-schema repository](https://github.com/home-assistant/ui-schema/issues).

## Cards
Cards are the smallest unit of organisation, and provide a great setup to group functionality. 

- [camera-preview](card-camera-preview.md)
- [entities](card-entities.md)
- [entity-filter](card-entity-filter.md)
- [glance](card-glance.md)
- [history-graph](card-history-graph.md)
- [horizontal-stack](card-horizontal-stack.md)
- [iframe](card-iframe.md)
- [markdown](card-markdown.md)
- [media-control](card-media-control.md)
- [picture-elements](card-picture-elements.md)
- [picture-entity](card-picture-entity.md)
- [picture-glance](card-picture-glance.md)
- [plant-status](card-plant-status.md)
- [vertical-stack](card-vertical-stack.md)
- [weather-forecast](card-weather-forecast.md)

You can also have custom cards now. The way to add custom cards is [really easy](https://developers.home-assistant.io/docs/en/lovelace_custom_card.html)!

## Views
These are exactly as before, tab views with icons or text that help you manage large dashboards with many entities. The views have now deep links like `/lovelace/3`. You can also assign your own custom id.

![views](https://user-images.githubusercontent.com/7738048/41777460-0c432b6e-7634-11e8-8738-ca078a552d06.gif)

Examples:

Without icon:
```yaml
views:
- title: Home
```

With icon and hover text:
```yaml
views:
- icon: mdi:settings
  id: debug
  title: Debugging
```

> The view above will be accessible using `/lovelace/debug`

### Known issues

- Theme is currently only partially usable (font color works)

## Migration scripts

Thare are two migration scripts:

- Thanks to [@OttoWinter](https://github.com/OttoWinter) for the [migration script](https://gist.github.com/OttoWinter/730383148041824bc47786ea292572f8)
- Thanks to [@dale3h](https://github.com/dale3h) for the [migration script that works also for packages](https://github.com/dale3h/python-lovelace)


## Make Lovelace default

To make the Lovelace UI the default dashboard view use one of the methods below.

### Using UI

Click the `>> Set lovelace as default page page on this device <<` in `dev-info` panel to make Lovelace the default interface when visiting `/`. 

### Overview binding

This is a **hack** that will bind `/lovelace` to **Overview** option in the menu instead of `/states` using javascript. It will also set default dashboard for `/` using the same mechanic as **Using UI** method. 

> Forcing your path to `/states` will still load the old dashboard page

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
  extra_html_url:
    - /local/lovelace.html
```

3. Restart your Home Assistant and force a clear cache on your browser and a few force reloads on IOS app

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
      card:
        title: All entities
```

## Example
To get you started you can use the `demo` platfrom in your `configuration.yaml`. There are many examples found [here](https://github.com/home-assistant/ui-schema/blob/master/dev_repo_test_config)
