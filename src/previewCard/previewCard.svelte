<script>
    export let backgroundSource = false;
    export let primaryText = false;
    export let subText = false;
    export let altText = "preview image";
    export let disabled = false;

    let maxHeight = 180;
    if (!primaryText) maxHeight += 20;
    if (!subText) maxHeight += 20;
    maxHeight = `${maxHeight}px`;
</script>

<!-- styling: primary-color, text-color, background-color, focus-color, active-color -->
<style>
    .card {
        height: 250px;
        width: 220px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        margin: 10px;
        transition-duration: 500ms;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.1);
        cursor: pointer;
        border: none;
        outline:none;
        background: var(--background-color, white);
        line-height: 1em;
        padding: 0px;
        -webkit-user-select: none; /* Safari */
        -ms-user-select: none; /* IE 10+ and Edge */
        user-select: none; /* Standard syntax */
        
    }

    button.card:hover {
        transition-duration: 500ms;
        box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.4);
    }

    button.card:focus {
        background: var(--focus-color, white);
    }

    button.card:active {
        background: var(--active-color, lightgrey)
    }

    .card::-moz-focus-inner {
        border: 0;
    }

    img {
        display: flex;
        max-width: 180px;
        max-height: var(--height);
        transition-duration: 500ms;
        margin-left: auto;
        margin-right: auto;
        opacity: .9;
        outline: 1px solid transparent;
    }

    .card:hover img {
        opacity: 1;
        transition-duration: 500ms;
        outline: 1px solid transparent;
    }

    .primary-text {
        text-align: center;
        color: var(--primary-text-color, black);
        font-size: 20px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .sub-text {
        text-align: center;
        color: grey;
        color: var(--secondary-text-color, gray);
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }

    .footer {
        margin: auto;
        width: 220px;
        line-height: 1.5em;
    }

    .hover {
        margin-top: auto;
        margin-bottom: auto;
        width: 220px;
    }

</style>


{#if disabled}
    <span class="card">
        {#if backgroundSource !== false}
            <div class="hover">
                <img src={backgroundSource} alt={altText} style="--height:{maxHeight}">
            </div>
        {/if}
        <div class="footer">
            {#if primaryText}
                <div class="primary-text" >{primaryText}</div>
            {/if}
            {#if subText}
                <div class="sub-text">{subText}</div>
            {/if}
        </div>
    </span>
{:else}
    <button class="card" on:click>
        {#if backgroundSource !== false}
            <div class="hover">
                <img src={backgroundSource} alt={altText} style="--height:{maxHeight}">
            </div>
        {/if}
        <div class="footer">
            {#if primaryText}
                <div class="primary-text" title={primaryText}>{primaryText}</div>
            {/if}
            {#if subText}
                <div class="sub-text" title={subText}>{subText}</div>
            {/if}
        </div>
    </button>
{/if}