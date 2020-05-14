# Material Table

Simple table and row components with some material styling. This is not the cleanest component to use, but it's written in a way to allow the user complete control over styling which I've not seen other svelte tables.

## Usage

```javascript
<MaterialTable items={styleList} columnSizes={["10%", "40%", "60%"]} height="500px">
    <div slot="header">
        <MaterialTableRow values={["#", "Name", "Style"]} type="header"/>
    </div>
    <div slot="item" let:item let:index>
        <MaterialTableRow
            values={[`${index + 1}.`, item.title, item.attributes]}
            type="click row"
            on:click={() => selectStyle(index)}
        />
    </div>
</MaterialTable>
```
Make sure to include `<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">` in your application for the icons if you have expandable rows.

The children aspect of this table relies on using svelte's `let:item` and `let:index` after passing in an array to the parent `MaterialTable` component, that way the user can specify how they want each row inside the `MaterialTableRow` element.

## Exposed Slots:
Name | Description
--- | ---
`header` | Top row of the table, expects a `MaterialTableRow`
`item` | Slot that is iterated over for each item in the table's list, exposes `let:item` and `let:index`

Exposed Events: `on:click`

#### Required props:
Prop | Description | Type
--- | --- | ---
`items` | Array to generate the table from | Object[]
`columnSizes` | Sizes `px/%` for each of the columns in the table, this carries over to the rows | String[]

#### Optional settings:
Param | Description | Type
--- | --- | ---
`height`| Height of the table, will use vertical scrolling after that point. | String

## Styling

Uses `--secondary-text-color`



# Material Table Row

Detailed explanation of using the rows, and nested tables.

## Usage

```javascript
<MaterialTable items={seriesData} columnSizes={["100%"]}>
    <div slot="header">
        <MaterialTableRow
            values={[$currentSeries]}
            on:click={() => selectItem({})}
            type="click header"
        />
    </div>
    <div slot="item" let:item={volume} let:index={volumeIndex}>
        <MaterialTableRow
            values={[`Volume ${volumeIndex+1}`]}
            on:click={() => selectItem({ volume: volume.id })}
            type="click row expand"
        >
            <div slot="children">
                <MaterialTable items={volume.chapters} columnSizes={["90%"]}>
                    <div slot="item" let:item={chapter} let:index={chapterIndex}>
                        <MaterialTableRow
                            values={[`Chapter ${chapterIndex+1}`]}
                            on:click={() => selectItem({ volume: volume.id, chapter: chapter.id, title: chapter.title })}
                            type="click row expand"
                            depth=1
                        >
                            <div slot="children">
                                <MaterialTable items={chapter.pages} columnSizes={["100%"]}>
                                    <div slot="item" let:item={page} let:index={pageIndex}>
                                        <MaterialTableRow
                                            values={[`Page ${pageIndex+1}`]}
                                            on:click={() => selectItem({ volume: volume.id, chapter: chapter.id, page: page.id, title: chapter.title })}
                                            type="click row"
                                            depth=5
                                        />
                                    </div>
                                </MaterialTable>
                            </div>
                        </MaterialTableRow>
                    </div>
                </MaterialTable>
            </div>
        </MaterialTableRow>
    </div>
</MaterialTable>
```

#### Required props:
Prop | Description | Type
--- | --- | ---
`values` | Array of objects to display (same length as `columnSizes`), can use the `item` and `index` exposed to the `item` slot | Object[]

#### {type} prop options, can have more than one at a time:
Param | Description
--- | ---
`row` | Gives it a border styling (default).
`click`| Will make the cursor a pointer and have a hover color.
`expand` | Will add a toggle button to display the `children` slot.