<script>
    export let state;
    export let xtend = false;
    export let searchValue = "";
    export let Updater;
    export let clearer;

    let Value = true;
    function handleKd(event) {}

    function extend() {
        if (xtend == false) {
            Value = !Value;
        }
        xtend = true;
    }

    function clearSearch() {
        document.querySelector("input").value = "";
        xtend = false;
        Value = true;
        clearer();
    }

    function getSearch() {
        let em = document.querySelector("input");
        searchValue = em.value;
        Updater(searchValue);
    }
</script>

<div class={state ? "topNav" : "navFocus"}>
    {#if xtend == false}<!---->{:else if xtend == true}
        <div class="cancel" on:click={clearSearch} on:keydown={handleKd} />
    {/if}
    <div
        on:click={extend}
        on:keydown={handleKd}
        class="search {Value ? '' : 'search-h'}"
    >
        <input
            type="search"
            placeholder="search..."
            class="i {Value ? '' : 'd'}"
            id="isearch"
        />
    </div>
    <div class="page-title {Value ? '' : 'pt-r'}">
        <h3 class="--title">Home</h3>
    </div>
    <div
        class="notifications {Value ? '' : 'notifications-h'}"
        on:click={getSearch}
        on:keydown={handleKd}
    />
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
        width: 9%;
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
    }

    .search:after {
        display: block;
        padding-bottom: 100%;
        content: "";
        margin-left: 1%;
    }

    .search-h {
        width: 80%;
        background: none;
        margin-left: 2%;
        transition: ease-in-out 0.3s;
    }

    .search-h:after {
        display: block;
        padding-bottom: 0%;
        content: "";
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
        width: 9%;
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

    .notifications:after {
        display: block;
        padding-bottom: 100%;
        content: "";
    }

    .pt-r {
        display: none;
    }

    .notifications-h {
        background-image: var(--searchUrl);
    }

    .i {
        width: 100%;
        padding-top: 3.8%;
        padding-bottom: 3.8%;
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
        display: flex;
        align-self: center;
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 3vw;
        color: var(--wtb);
        opacity: 0.55;
    }

    /* Select the search cancel button */
    input[type="search"]::-webkit-search-cancel-button {
        display: none;
    }

    .cancel {
        width: 9%;
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

    .cancel:after {
        display: block;
        padding-bottom: 100%;
        content: "";
    }
</style>
