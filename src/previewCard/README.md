# Svelte-preview-card

Basic card presenting a title, sub-text, and background image ideally for a grid layout. Also has an event emitter for when it has been clicked.

## Usage

```
let src = "my_picture.png";
<PreviewCard
    background_source={src}
    primary_text="Title"
    sub_text="My Picture"
></PreviewCard>
```


#### Exposed Events:

Event | Description
-- | --
`on:click` | When the card is clicked

#### Optional settings:

Param | Description | Type
--- | --- | ---
`background_source` | Source for the card's image, defaults to none | String
`primary_text` `sub_text` | Displayed text values, if these are not used the image max-height is increased. | String
`alt_text` | Alt text for the image | String
`disabled` | Whether to disable the card from being clicked | Boolean

## Styling

Uses `--primary-color, --secondary-text-color, --background-color, --focus-color, --active-color