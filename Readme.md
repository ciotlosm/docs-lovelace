# Lovelace UI 

<img align="right" height="250px" src="https://user-images.githubusercontent.com/7738048/41777567-6f8caa1a-7634-11e8-8ff4-a0589240d724.png">

Below you will find different types of cards available in the new **Lovelace UI** for [Home Assistant](https://www.home-assistant.io/).

For more in depth documentation on entities, please visit the [developer documentation for Lovelace UI](https://developers.home-assistant.io/docs/en/lovelace_index.html)

The UI is structured in views and a view contains cards as seen on the example in the developer documentation.

> To access **lovelace** please go to `dev-info` and click the link '**Try out the new Lovelace UI (experimental)**' or use the "hack" below


## Make Lovelace UI default
This method uses a hack (that you can easily remove later) that will just force navigation to `/lovelace` everytime you navigate to `/status`

### Steps

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

**MAGIC!**


## Migration script
Thanks to @OttoWinter_ for the [migration script](https://gist.github.com/OttoWinter/730383148041824bc47786ea292572f8) from the old interface.


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


## Other changes
- Glance card ratio fixes on picture icon
- Glance card title bug - text is no longer overflow elipsis and text now overlaps