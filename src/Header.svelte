<script>
    export let page = 0;
    export let topNavVisible;
</script>

{#if page == 0}
    <div class="header">
        <div class="text"><h3 class="--text">For You</h3></div>
        <div class="reload" />
    </div>
{:else if page == 1}
    <div class="header">
        <div class="text"><h3 class="--text">Search Results</h3></div>
        <div class="reload" style="opacity:0;" />
    </div>
{:else if page == 2}
    <div class="header">
        <div class="text"><h3 class="--text">New Notifications</h3></div>
        <div class="reload" />
    </div>
{/if}

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --wtb: white;
            --wtbo: rgba(255, 255, 255, 0.772);
            --reloadUrl: url("./../reload.png");
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --wtb: rgb(0, 0, 0);
            --wtbo: rgba(0, 0, 0, 0.772);
            --reloadUrl: url("./../reload_B.png");
        }
    }

    .header {
        width: 100%;
        height: 4%;
        margin-top: 8%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: row;
    }
    .text {
        width: 80%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 3%;
    }

    .--text {
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 4vw;
        color: var(--wtb);
    }
    .reload {
        width: 17%;
        height: 100%;
        background-image: var(--reloadUrl);
        background-size: 25%;
        background-repeat: no-repeat;
        background-position: center;
    }
</style>
