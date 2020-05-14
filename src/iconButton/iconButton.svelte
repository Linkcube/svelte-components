<script>
    export let icon;
    export let title = "";
    export let scaleX = 1;
    export let scaleY = 1;
</script>

<!-- Styling: text-color -->
<style>
    .material-icons {
        font-size: 24px;
        color: var(--secondary-text-color, gray);
        background-color: rgba(0,0,0,0);
        border: none;
        padding-left: 10px;
        padding-right: 10px;
        cursor: pointer;
        transition: 0.3s;
        border-radius:100px;
        -webkit-user-select: none; /* Safari */
        -ms-user-select: none; /* IE 10+ and Edge */
        user-select: none; /* Standard syntax */
        margin-bottom: 7px;
        -webkit-transform: scaleX(var(--scaleX)) scaleY(var(--scaleY));
        transform: scaleX(var(--scaleX)) scaleY(var(--scaleY));
    }

    .material-icons::-moz-focus-inner {
        border: 0;
    }

    .material-icons:hover {
        box-shadow: 0px 6px var(--secondary-text-color, gray);
    }
</style>

<div>
    <button
        title={title}
        class="material-icons"
        style="--scaleX:{scaleX}; --scaleY:{scaleY}"
        on:click
        on:dragenter
        on:dragover
        on:drop
    >{icon}</button>
</div>