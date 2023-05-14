<script>
    export let state;
    export let page = 0;
    export let searchValue = "";
    export let sUpdater;
    export let nUpdater;
    export let clearer;

    let Value = true;
    let st = false;

    const deviceWidth = window.innerWidth;

    function handleKd(event) {}

    function esearch() {
        if (page != 1) {
            Value = !Value;
        }
        page = 1;
    }

    function clearSearch() {
        document.querySelector("input").value = "";
        page = 0;
        Value = true;
        clearer();
    }

    function getSearch() {
        let em = document.querySelector("input");
        searchValue = em.value;
        sUpdater(searchValue);
    }

    function enotif() {
        if (page != 2) {
            Value = !Value;
        }
        page = 2;
    }

    function clearNotif() {
        document.querySelector("input").value = "";
        page = 0;
        Value = true;
        clearer();
    }

    function getNotif() {
        let em = document.querySelector("input");
        searchValue = em.value;
        nUpdater();
    }

    function handleKeyPress(event) {
        if (event.key === "Enter" || event.keyCode === 13) {
            getSearch();
        }
    }
</script>

<div class={state ? "topNav" : "navFocus"}>
    <!---->
    {#if page == 0}<!---->{:else if page == 1}
        <div class="cancel" on:click={clearSearch} on:keydown={handleKd} />
    {:else if page == 2}
        <div class="cancel" on:click={clearNotif} on:keydown={handleKd} />
    {/if}
    <div
        on:click={esearch}
        on:keydown={handleKd}
        class="search {Value ? '' : page == 2 ? 'search-d' : 'search-h'}"
    >
        <input
            type="search"
            placeholder="search..."
            class="i {Value ? '' : 'd'}"
            id="isearch"
            on:keydown={handleKeyPress}
        />
    </div>
    <div class="page-title {Value ? '' : 'pt-r'}">
        <h3 class="--title">Home</h3>
    </div>
    {#if page == 1}
        <div
            class="notifications {Value ? '' : 'notifications-h'}"
            on:click={getSearch}
            on:keydown={handleKd}
        />
    {:else if page == 0}
        <div
            class="notifications {Value ? '' : 'notifications-h'}"
            on:click={enotif}
            on:keydown={handleKd}
        />
    {/if}
</div>

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --wtb: white;
            --wtbo: rgba(255, 255, 255, 0.772);
            --bellUrl: url("./../bell.png");
            --searchUrl: url("./../search.png");
            --xUrl: url("./../x.png");
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --wtb: rgb(0, 0, 0);
            --wtbo: rgba(0, 0, 0, 0.772);
            --bellUrl: url("./../bell_B.png");
            --searchUrl: url("./../search_B.png");
            --xUrl: url("./../x.png");
        }
    }

    .topNav {
        width: 100%;
        height: 5.5%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        margin-top: 5%;
        transition: ease-in-out 0.3s;
    }

    .navFocus {
        margin-top: -13.5%;
        width: 100%;
        height: 5.5%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
    }

    .search {
        width: 2.2rem;
        height: 2.2rem;
        border: 0.6vw solid #5533ebde;
        border-radius: 8px;
        align-self: center;
        justify-self: flex-start;
        justify-content: flex-start;
        margin-left: 3%;
        transition: ease-in-out 0s;
        margin-right: 1%;
        background-image: var(--searchUrl);
        background-size: 60% 60%;
        background-repeat: no-repeat;
        background-position: center;
        opacity: 1;
    }

    .search-h {
        width: 72%;
        height: 2.2rem;
        background: none;
        margin-left: 2%;
        transition: ease-in-out 0.3s;
        opacity: 1;
    }

    .search-d {
        width: 85%;
        height: 2.2rem;
        background: none;
        margin-left: 2%;
        transition: ease-in-out 0.3s;
        opacity: 0;
    }

    .page-title {
        width: 24%;
        height: 9%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-left: auto;
        margin-right: auto;
        color: var(--wtb);
    }

    .--title {
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 4.6vw;
    }

    .notifications {
        width: 2.2rem;
        height: 2.2rem;
        border: 0.6vw solid var(--wtbo);
        border-radius: 8px;
        align-self: center;
        justify-content: flex-end;
        margin-right: 3%;
        margin-left: 1%;
        background-image: var(--bellUrl);
        background-size: 60% 60%;
        background-repeat: no-repeat;
        background-position: center;
        transition: ease-in-out 0.3s;
    }

    .pt-r {
        display: none;
    }

    .notifications-h {
        background-image: var(--searchUrl);
    }

    .i {
        width: 100%;
        height: 100%;
        background-color: transparent;
        border-style: none;
        outline: none;
        display: none;
        border-radius: 5px;
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 3vw;
        padding-left: 2%;
        color: var(--wtb);
    }

    .d {
        display: block;
    }

    ::placeholder {
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 3.5vw;
        color: var(--wtb);
        opacity: 0.55;
    }

    /* Select the search cancel button */
    input[type="search"]::-webkit-search-cancel-button {
        display: none;
    }

    .cancel {
        width: 2.2rem;
        height: 2.2rem;
        border: 0.6vw solid red;
        border-radius: 8px;
        align-self: center;
        justify-content: flex-end;
        margin-right: 1%;
        margin-left: 3%;
        background-image: var(--xUrl);
        background-size: 50% 50%;
        background-repeat: no-repeat;
        background-position: center;
        transition: ease-in-out 0.3s;
    }
</style>
