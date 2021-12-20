<script>
    export const navbar = undefined
    let open = false
    function toggleOpen() {
        if (!open) {
            open = true
        } else {
            open = false;
        }
    }
</script>

<navbar>
    <button>Home</button>
    <button on:click={toggleOpen}>About</button>
    {#if open}
    <p class=about>Hoi</p>
    {/if}
</navbar>

<style>
    navbar {
        background: gainsboro;
        width: 100vw;
        height: 5vh;
        position: absolute;
    }

    .about {
        width: 100px;
        height: 100px;
        background: gainsboro;
    }
</style>