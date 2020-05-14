# Icon Button

Basic button that uses the material icons iconsheet. Has a circular box shadow that pops up beneath the element on hover.

## Usage

```javascript
<IconButton
    icon="expand_more"
    title="Show More"
    on:click={show}
/>
```

Make sure to include `<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">` in your application for the icons.

Exposed Events: `on:click` `on:dragenter` `on:dragover` `on:drop`

#### Required props:
Prop | Description | Type
--- | --- | ---
`icon` | Material icon to use | String


#### Optional settings:
Param | Description | Type
--- | --- | ---
`title`| Title to display when hovered on. | String
`scaleX` | How much to scale on the X-axis | Number
`scaleY` | How much to scale on the Y-axis | Number

## Styling

Uses `--secondary-text-color`