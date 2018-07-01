### Iframe

Iframe cards are useful to embed outside websites in your dashboard with little effort. One such example is a grafana view. You can also embed files stored in your `config/www` folder and reference them using `/local/<file>`.

<img width="500" alt="iframe" src="https://user-images.githubusercontent.com/7738048/41901303-d47da286-7930-11e8-8ea2-8620dd81f918.png">

> Make sure the URL you're embedding has the right protocol and allows to be embedded in an iframe on a different domain. For example if your Home Assistant setup uses https you won't be able to embed http URLs

**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `iframe`
| url | string | **Required** | iframe source url
| aspect_ratio | string | `"50%"` | Iframe height-width-ratio
| title | string | Optional | Card title

**Examples**

```yaml
      - type: iframe
        url: https://worldpingdemo.grafana.net/d/000000027/worldping-endpoint-summary?var-endpoint=www_amazon_com&var-probe=All&panelId=2&fullscreen&orgId=3&theme=light
        aspect_ratio: 100%
```

Local html for custom content. Place `example.html` in your `config/www` folder and reference it as below:
```yaml
      - type: iframe
        url: /local/example.html
        title: Sample local file
```