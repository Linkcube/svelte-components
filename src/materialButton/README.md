# Material Button

Material styled button using svelte.

## Usage

```javascript
<MaterialButton value="Click Me!" on:click={addValue}/>
```

Exposed Events: `on:click` `on:dragenter` `on:dragover` `on:drop`

#### Required props:
Prop | Description | Type
--- | --- | ---
`value` | Text displayed in the button | String

## Styling

Uses `--secondary-text-color, --secondary-color`