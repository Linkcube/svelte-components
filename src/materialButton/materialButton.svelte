<script>
    export let value;
</script>

<!-- Styling: text-color, secondary-color -->
<style>
    
    div {
        display: flex;
        line-height: 40px;
        margin-left: 5px;
        margin-right: 5px;
    }

    .container {
        color: var(--primary-text-color, black);
        border: 1px var(--secondary-color, lightgray) solid;
        padding-left: 10px;
        padding-right: 10px;
        border-radius: 5px;
        height: 40px;
        cursor: pointer;
        margin-top: auto;
        margin-bottom: auto;
        -webkit-user-select: none; /* Safari */
        -ms-user-select: none; /* IE 10+ and Edge */
        user-select: none; /* Standard syntax */
    }

    .container:hover {
        background: var(--secondary-color, lightgray);
        transition-duration: 400ms;
    }
</style>
<div>
    <span class="container" on:click on:dragenter on:dragover on:drop>{value}</span>
</div>