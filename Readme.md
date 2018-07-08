# Lovelace UI

:star: Please use [official docs](https://www.home-assistant.io/)

## [Changelog](changelog.md)

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

## Unused entities
To see what entities you left out, you can now use the menu `Unused entities` in the header of Lovelace,  the top right corner.

![unused-entities](https://user-images.githubusercontent.com/7738048/42287697-0f1dfe00-7fc0-11e8-99ee-f5b312767879.png)

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
