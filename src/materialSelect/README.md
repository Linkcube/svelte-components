# Material Select

Select element with material style using svelte, the dropdown options are still based on the browser.

## Usage

```javascript
<MaterialSelect bind:value={selection} label="Pick One">
    {#each myList as myItem, index}
        <option value={index}>{myItem}</option>
    {/each}
</MaterialSelect>
```

Exposed Events: `on:blur` `on:change` `on:input`

#### Optional settings:
Param | Description | Type
--- | --- | ---
`label` | Hovering label text | String

## Styling

Uses `--primary-color, --secondary-color, --background-color, --highlight-color`