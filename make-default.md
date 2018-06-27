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