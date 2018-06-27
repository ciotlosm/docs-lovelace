### [Weather forecast](https://developers.home-assistant.io/docs/en/lovelace_card_types.html#weather-forecast)

Weather forecast is a card to display the weather. Very useful to include on interfaces that people display on the wall. 

![weather-forecast](https://user-images.githubusercontent.com/7738048/41775906-731ad130-762e-11e8-854f-d156a0ff56ef.png)

Example:
```yaml
- type: weather-forecast
  entity: weather.demo_weather_north
```