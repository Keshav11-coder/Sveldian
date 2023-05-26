<script>
    let prevScrollPos = window.pageYOffset;
    let timeoutId;
    function keyDown(event) {}
    let sval = "";
    let returnedItems = []; //NOTE: THIS VARIABLE IS TEMPORARY. there will be replacements placed in the future, meaning this is NOT the official solution
    const deviceWidth = window.innerWidth;

    export let topNavVisible = true;
    export let page = 0;

    export let search = false;

    export const callSearchClear = function callSearchClear() {
        sval = "";
    };

    let items = [];
    let results = [];

    async function get_search(searchString) {
        console.log(searchString)
        let url = `http://localhost:3000/api?database=skilldian&collection=search&amount=50&search=`+searchString;
        const response = await fetch(url);
        var data = await response.json();
        console.log(data);
        console.log("data");
        search = true;

        results = data;
    }

    async function get_items(url) {
        url = `http://localhost:3000/api?database=skilldian&collection=suggested&amount=50`;
        const response = await fetch(url);
        var data = await response.json();
        console.log(data);
        search = false;

        items = data;
    }

    get_items();

    let notifications = [];

    export const sUpdater = function sUpdater(data) {
        if (data != "") {
            sval = data;

            get_search(data);
        } else {
            
        }
    };

    export const nUpdater = function nUpdater() {
        if (page == 2) {
            returnedItems = updateContent(notifications);
        }
    };

    function handleScroll(event) {
        let currentScrollPos = event.target.scrollTop;
        if (prevScrollPos > currentScrollPos) {
            if (!topNavVisible) {
                //clearTimeout(timeoutId);
                topNavVisible = true;
            }
        } else {
            if (topNavVisible) {
                //timeoutId = setTimeout(() => {
                topNavVisible = false;
                //}, 250); // adjust the delay time as needed
            }
        }
        prevScrollPos = currentScrollPos;
    }

    function updateContent(items) {
        items = [...items];
        return items;
    }
</script>

<div class="wrapper0 {topNavVisible ? '' : 'wrapper1'}">
    <div class="content" on:scroll={handleScroll} id="content">
        {#if !search}
            {#each items as item}
                <div class="container" id="UIDSCI-0000">
                    <div class="im">
                        <img class="image" src={item.url} alt="logo" />
                    </div>
                    <div class="item" style="border: 0.25vw solid {item.oc};">
                        <div class="opp">
                            <h3 class="opp-text">{item.opp}</h3>
                        </div>
                        <div class="company">
                            <h3 class="cn-text">@{item.cc}</h3>
                        </div>
                    </div>
                    <div class="forward" style="border: 0.25vw solid {item.oc}">
                        <i class="fa-regular fa-solid fa-caret-right fa-2x" />
                    </div>
                </div>
            {/each}
        {:else if search}
            {#each results as item}
                <div class="container" id="UIDSCI-0000">
                    <div class="im">
                        <img class="image" src={item.url} alt="logo" />
                    </div>
                    <div class="item" style="border: 0.25vw solid {item.oc};">
                        <div class="opp">
                            <h3 class="opp-text">{item.opp}</h3>
                        </div>
                        <div class="company">
                            <h3 class="cn-text">@{item.cc}</h3>
                        </div>
                    </div>
                    <div class="forward" style="border: 0.25vw solid {item.oc}">
                        <i class="fa-regular fa-solid fa-caret-right fa-2x" />
                    </div>
                </div>
            {/each}
        {/if}
    </div>
</div>

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --color: white;
            --cscheme: black;
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --color: black;
            --cscheme: white;
        }
    }

    .wrapper0 {
        width: 100%;
        height: 70vh;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
        margin-top: 7%;
    }

    .wrapper1 {
        width: 100%;
        height: 80vh;
        margin-top: 7%;
        display: flex;
        align-items: center;
        transition: ease-in-out 0.3s;
        justify-content: center;
    }

    .content {
        width: 100%;
        padding-left: 30%;
        padding-right: 30%;
        height: 98%;
        overflow-y: scroll;
        padding-bottom: 10%;
    }

    @keyframes fadeInUp {
        0% {
            transform: translateX(100%);
            opacity: 0;
        }

        100% {
            transform: translateX(0);
            opacity: 1;
        }
    }

    .container {
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 8rem;
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        margin-bottom: 2.4%;
    }

    .im {
        width: 8rem;
        height: 8rem;
        position: relative;

        margin-top: auto;
        margin-bottom: auto;
    }

    .image {
        width: 100%;
        height: 100%;
        border-radius: 1vw 0px 0px 1vw;
    }

    .item {
        border: 0.35vw solid #3b5998;
        border-radius: 0 1vw 1vw 0;
        box-sizing: border-box;
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 100%;
        width: 60%;
        /*box-shadow: -6px 0px 35px 0px rgba(0, 0, 0, 0.75);*/
    }

    .opp {
        width: 100%;
        height: 50%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 5%;
    }

    .opp-text {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 1.5vw;
        color: var(--color);
        opacity: 0.9;
    }

    .company {
        width: 100%;
        height: 50%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 5%;
    }

    .cn-text {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 1.3vw;
        color: var(--color);
        opacity: 0.75;
    }

    .forward {
        width: 19%;
        height: 100%;
        margin-left: 2%;
        border-radius: 1vw;
        box-sizing: border-box;

        display: flex;
        align-items: center;
        justify-content: center;
    }

    .fa-caret-right {
        color: var(--color);
    }

    .item:nth-child(2) {
        animation-delay: 0.1s;
    }

    .item:nth-child(3) {
        animation-delay: 0.2s;
    }

    .item:nth-child(4) {
        animation-delay: 0.3s;
    }

    .item:nth-child(5) {
        animation-delay: 0.4s;
    }

    .item:nth-child(6) {
        animation-delay: 0.5s;
    }

    /* scrollbar track */
    ::-webkit-scrollbar-track {
        display: none;
    }

    /* scrollbar thumb */
    ::-webkit-scrollbar-thumb {
        display: none;
    }

    /* scrollbar corner */
    ::-webkit-scrollbar-corner {
        display: none;
    }

    /* scrollbar width and height */
    ::-webkit-scrollbar {
        display: none;
    }

    .fa-caret-right {
        color: var(--color);
    }
</style>
