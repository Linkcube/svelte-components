# Material Input

Text Area input with material styling using svelte, has a hovering label that fills the input until the user selects the element or has text in it. Also has a sub text hint field for additional info.

## Usage

```javascript
<MaterialTextArea
    label="Text"
    bind:value={text}
    height=200
    width=270
    resize="none"
/>
```


#### Exposed Events:
Event | Description
--- | ---
`on:blur` | Default js event


#### Optional settings:
Param | Description | Type
--- | --- | ---
`height`| Default height of the text area element. | String
`width` | Default width of the text area element. | String
`resize` | Resize ability of the text area | String
`label` | Hovering label text | String
`hintText` | Text present beneath the input | String

## Styling

Uses `--primary-color, --secondary-color, --secondary-text-color, --background-color, --highlight-color`