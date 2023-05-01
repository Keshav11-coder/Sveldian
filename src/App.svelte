<script>
    import TopNav from "./TopNav.svelte";
    import Header from "./Header.svelte";
    import Content from "./Content.svelte";
    import { null_to_empty } from "svelte/internal";

    let topNavVisible = true;
    let xtend = false;

    let sUpdater;
    let callSearchClear;
</script>

<div class="wrapper">
    <TopNav Updater={sUpdater} clearer={callSearchClear} state={topNavVisible} bind:xtend />
    <Header bind:xtend />
    <Content bind:sUpdater bind:topNavVisible bind:xtend bind:callSearchClear />
</div>

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --uniColor: white;
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --uniColor: black;
        }
    }

    .wrapper {
        width: 100vw;
        height: 98vh;
    }
</style>
