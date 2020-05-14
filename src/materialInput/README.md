# Material Input

Text input with material styling using svelte, has a hovering label that fills the input until the user selects the element or has text in it. Also has a sub text hint field for additional info.

## Usage

```javascript
<MaterialInput
    label="Enter a name" 
    hintText="First and last"
    bind:value={newName} 
    on:enter={addName}
/>
```


#### Exposed Events:
Event | Description
--- | ---
`on:blur` | Default js event
`on:enter` | Fires when the user hits the `enter` key while typing in the box


#### Optional settings:
Param | Description | Type
--- | --- | ---
`value`| Value of the input element, can set a default. | String
`id` | Input element's ID | String
`label` | Hovering label text | String
`hintText` | Text present beneath the input | String

## Styling

Uses `--primary-color, --secondary-color, --background-color, --highlight-color`