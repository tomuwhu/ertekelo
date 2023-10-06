<script>
    import { base } from '$app/paths'
    export let active
    const mpl = [
        {
            n: 'Kezdőoldal',
            h: ''
        },
        {
            n: 'Cica',
            h: 'cica'
        },
        {
            n: 'Kutya',
            h: 'kutya'
        }
    ]
</script>
<div class="mh">
    {#each mpl as mp}
        {#if mp.n != active}
        <a href="{base}/{mp.h}">{mp.n}</a>
        {:else}
        <b>{mp.n}</b>
        {/if}
    {/each}
    
</div>
<style>
    .mh {
        background-color: black;
        color: gray;
        position: absolute;
        bottom: 0px;
        user-select: none;
        font-size: 30px;
    }
    .mh a {
        all: unset;
        padding: 6px;
        cursor: pointer;
    }
    .mh a:hover {
        color: yellow;
    }
    .mh a:active {
        color: rgb(243, 173, 241);
    }
    b {
        color: black;
        background-color: white;
    }
    a, b {
        padding-left: 20px;
        padding-right: 20px;
    }
</style>