<script>
    import { onMount } from 'svelte';

    export let value;
    export let label = "";

    let width = 140;
    let selectEl;

    function updateSize() {
        if (selectEl && selectEl.selectedOptions.length > 0) {
            let textLen = selectEl.selectedOptions[0].label.length;
            if (label.length === 0) {
                width = 40 + (10 * textLen);
            } else if (label.length < textLen) {
                width = Math.max(10 * textLen, 140);
            } else {
                width = 140;
            }
        } else {
            if (label.length === 0) {
                width = 40 + (10 * JSON.stringify(value).length);
            } else if (label.length > 12) {
                width = 10 * label.length;
            }
        }
    }

    function scale(node, value) {
        return {
            update(value) {
                updateSize();
            },
            destroy() {}
        }
    }

    onMount(updateSize);
</script>

<!-- Styling: --primary-color, --secondary-color, --background-color, --highlight-color -->
<style>
    .form-field {
        display: flex;
        flex-direction: column;
        line-height: 40px;
        margin-top: auto;
        margin-bottom: auto;
    }

    .form-field-control {
        display: flex;
        flex-shrink: 1;
        border-radius: 8px 8px 0 0;
        position: relative;
        width: 100%;
    }

    select {
        margin: 8px;
        height: 40px;
        color: var(--primary-text-color, black);
        background: var(--background-color, white);
        background-image: none;
        box-sizing: border-box;
        margin: 0;
        border-radius: 5px;
        border-width: 2px;
        border-color: var(--secondary-color, lightgray);
        -moz-appearance: none;
        -webkit-appearance: none;
        appearance: none;
        min-width: var(--width);
        cursor: pointer;
    }
    
    select::-ms-expand {
        display: none;
    }
    
    select:hover {
        border-color: var(--highlight-color, yellow);
    }
    
    select:focus {
        transition-duration: 400ms;
        outline: none;
        border-color: var(--primary-color, #3c8bff);
    }

    .float-text {
        font-weight: normal;
        font-size: large;
        left: 0;
        margin: 0;
        padding-left: 15px;
        padding-top: 7px;
        position: absolute;
        top: 0;
        pointer-events: none;
        background: none;
        color: var(--secondary-text-color, gray);
        white-space: nowrap;
        overflow: hidden;
        
    }

    select:focus + .float-text {
        color: var(--primary-color, #3c8bff);
        transform: scale(.75, .75) translate(-10px, -30px);
        transition-duration: 400ms;
        padding: 0% 5% 0%;
        margin-left: 5%;
        background: var(--background-color, white);
        background-clip: padding-box;
    }

    select:not(:placeholder-shown) + .float-text {
        transform: scale(.75, .75) translate(-10px, -30px);
        transition-duration: 400ms;
        padding: 0% 5% 0%;
        margin-left: 5%;
        background: var(--background-color, white);
        background-clip: padding-box;
    }

    select:placeholder-shown + .float-text {
        transition-duration: 400ms;
    }

    .material-icons {
        color: var(--secondary-color, lightgray);
        margin: auto;
        margin-left: -30px;
        pointer-events: none;
    }

    select:focus + .material-icons {
         color: var(--primary-color, #3c8bff);
    }
</style>

<div class="form-field">
    <div class="form-field-control">
        <select
            bind:this={selectEl}
            bind:value={value}
            use:scale={value}
            style="--width: {width}px;"
            on:blur on:change on:input
        >
            <slot></slot>
        </select>
        <label class="float-text">{label}</label>
        <div class="material-icons">arrow_drop_down</div>
    </div>
</div>