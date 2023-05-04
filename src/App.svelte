<script>
    import TopNav from "./TopNav.svelte";
    import Header from "./Header.svelte";
    import Content from "./Content.svelte";

    let topNavVisible = true;
    let search = false;

    let sUpdater;
    let nUpdater;
    let callSearchClear;

    let page = 0; // 0,1,2,3 home,search,notifications,job details
</script>

<div class="wrapper">
    <TopNav
        sUpdater={sUpdater}
        nUpdater={nUpdater}
        clearer={callSearchClear}
        state={topNavVisible}
        bind:page
    />
    <Header bind:page />
    <Content
        bind:sUpdater
        bind:nUpdater
        bind:topNavVisible
        bind:search
        bind:callSearchClear
        page={page}
    />
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
