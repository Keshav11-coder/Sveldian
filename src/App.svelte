<script>
    import TopNav from "./TopNav.svelte";
    import Header from "./Header.svelte";
    import Content from "./Content.svelte";

    import TopNav_L from "./TopNav_L.svelte";
    import Header_L from "./Header_L.svelte";
    import Content_L from "./Content_L.svelte";
    import Menu from "./menu.svelte";
    import Guide from "./guide.svelte";

    let topNavVisible = true;
    let search = false;

    let sUpdater;
    let nUpdater;
    let callSearchClear;

    let page = 0; // 0,1,2,3 home,search,notifications,job details

    const deviceWidth = window.innerWidth;
</script>

<div class="wrapper">
    {#if deviceWidth < 1000}
        <TopNav
            {sUpdater}
            {nUpdater}
            clearer={callSearchClear}
            state={topNavVisible}
            bind:page
        />
        {#if page == 1}
        <Header bind:page bind:topNavVisible></Header>
        {/if}
        <Content
            bind:sUpdater
            bind:nUpdater
            bind:topNavVisible
            bind:callSearchClear
            {page}
        />
    {:else if deviceWidth > 1000}
        <Menu bind:topNavVisible/>
        <TopNav_L sUpdater={sUpdater} bind:search bind:topNavVisible/>
        <Header_L />
        <Content_L bind:search bind:topNavVisible bind:sUpdater />
        <Guide index=1></Guide>
    {/if}
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

    @media only screen and (min-width: 1000px) {
    }
</style>
