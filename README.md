# Linkcube's Svelte Components

A list of the custom components I've made for my svelte projects, moved them all into one shared repo so that it would be easier to maintain styling across all of them.

Demo: http://linkcube.github.io/

## Styling

Going with the :root route, all of these components use the following css variables to some extent when styling:
| Variable               | Default Value | 
|:---------------------- | -------------:|
| --primary-color        | lightblue     |
| --secondary-color      | lightgray     |
| --background-color     | white         |
| --priamry-text-color   | black         |
| --secondary-text-color | grey          |
| --highlight-color      | yellow        |
| --focus-color          | white         |
| --active-color         | lightgrey     |

## Usage

```javascript
import {
    AudioControls,
    IconButton,
    MaterialButton,
    MaterialInput,
    MaterialSelect,
    MaterialTable,
    MaterialTableRow,
    MaterialTextArea,
    PreviewCard
} from 'linkcube-svelte-components';
```
Each component has a readme detailing their individual uses, and what styling variables they make use of.

## Links

[Github](https://github.com/Linkcube/svelte-preview-card)
[NPM](https://www.npmjs.com/package/svelte-preview-card)
