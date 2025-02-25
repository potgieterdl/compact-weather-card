### This is a fork from https://github.com/bramkragten/weather-card, in a more compact form

# Lovelace animated weather card

Originally created for the [old UI](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008) converted by @arsaboo and @ciotlosm to [Lovelace](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008/291) and now converted to Lit to make it even better.

This card uses the awesome [animated SVG weather icons by amCharts](https://www.amcharts.com/free-animated-svg-weather-icons/).

![Weather Card](https://github.com/potgieterdl/compact-weather-card/blob/master/compact-weather-card.gif?raw=true)

Thanks for all picking this card up.

## Installation:

You have 2 options, hosted or self hosted (manual). The first option needs internet and will update itself.

### If you are using Firefox:

Firefox < 66 does not support all the needed functions yet for the editor.
You change this by enabling `javascript.options.dynamicImport` in `about:config`.

# Hosted:

Add the following to resources in your lovelace config:

```yaml
- url: https://cdn.jsdelivr.net/gh/potgieterdl/compact-weather-card/dist/compact-weather-card.js
  type: module
```

# Manual:

1. Download the [compact-weather-card.js](https://raw.githubusercontent.com/potgieterdl/compact-weather-card/master/dist/compact-weather-card.js) to `/config/www/custom-lovelace/compact-weather-card/`. (or an other folder in `/config/www/`)
2. Save, the [amCharts icons](https://www.amcharts.com/free-animated-svg-weather-icons/) (The contents of the folder "animated") under `/config/www/custom-lovelace/weather-card/icons/` (or an other folder in `/config/www/`)
3. If you use Lovelace in storage mode, and want to use the editor, download the [weather-card-editor.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card-editor.js) to `/config/www/custom-lovelace/weather-card/`. (or the folder you used above)

Add the following to resources in your lovelace config:

```yaml
resources:
  - url: /local/custom-lovelace/compact-weather-card/compact-weather-card.js
    type: module
```

## Configuration:

And add a card with type `custom:compact-weather-card`:

```yaml
type: custom:compact-weather-card
entity: weather.yourweatherentity
name: Optional name
```

If you want to use your local icons add the location to the icons:

```yaml
type: custom:weather-card
entity: weather.yourweatherentity
icons: "/local/custom-lovelace/weather-card/icons/"
```

You can choose wich elements of the weather card you want to show:

The 3 different rows, being:

- The current weather icon, the current temperature and title
- The details about the current weather
- The 5 day forecast

```yaml
type: custom:weather-card
entity: weather.yourweatherentity
current: true
details: false
forecast: true
```

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```

### Dark Sky:

When using Dark Sky you should put the mode to `daily` if you want a daily forecast with highs and lows.

```yaml
# Example configuration.yaml entry
weather:
  - platform: darksky
    api_key: YOUR_API_KEY
    mode: daily
```
