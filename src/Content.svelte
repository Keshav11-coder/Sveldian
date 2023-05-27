<script>
    let prevScrollPos = window.pageYOffset;
    let timeoutId;
    function keyDown(event) {}
    let sval = "";
    let returnedItems = []; //NOTE: THIS VARIABLE IS TEMPORARY. there will be replacements placed in the future, meaning this is NOT the official solution
    const deviceWidth = window.innerWidth;

    export let topNavVisible = true;
    export let page = 0;

    export const callSearchClear = function callSearchClear() {
        sval = "";
    };

    /*async function get(url) {
        const response = await fetch(url);
        var data = await response.json();
        console.log(data);
        items = data;
    }

    get("http://localhost:3000/api/");*/

    let notifications = [];

    let items = [
        // turn into fetch
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
    ];

    let results = [
        // turn into fetch
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
            type: "else",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
            type: "premium",
            description: `Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent blandit sem eu nisl fermentum ultrices. Duis suscipit auctor ex ac.`,
        },
    ];

    export const sUpdater = function sUpdater(data) {
        if (data != "" && page == 1) {
            sval = data;
            // client.js
            const searchString = "backend developer";

            returnedItems = results;
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

{#if page == 0}
    <div class="wrapper0 {topNavVisible ? '' : 'wrapper1'}">
        <div class="content" on:scroll={handleScroll} id="content">
            {#each items as item}
                <div
                    class="container{item.type == 'premium' ? '-premium' : ''}"
                    id="UIDSCI-0000"
                >
                    <div class="item-wrap">
                        <div
                            class="item{item.type == 'premium'
                                ? '-premium'
                                : ''}"
                        >
                            <div class="company">
                                <h3 class="cn-text">{item.cc}</h3>
                            </div>
                            <div class="opp">
                                <h3 class="opp-text">{item.opp}</h3>
                            </div>
                        </div>
                        {#if item.type == "premium"}
                            <div class="description">
                                <h3 class="description-text">
                                    {item.description}
                                </h3>
                            </div>
                        {/if}
                    </div>
                    {#if item.type == "premium"}
                        <div class="image-wrap">
                            <div class="im">
                                <img class="image" src={item.url} alt="logo" />
                            </div>
                            <div class="forward" style="border: 0.8vw solid {item.oc};">
                                <i
                                    class="fa-regular fa-solid fa-caret-right fa-1x"
                                />
                            </div>
                        </div>
                    {:else}
                        <div class="im-normal">
                            <img class="image" src={item.url} alt="logo" />
                        </div>
                        <div class="forward-normal" style="border: 0.8vw solid {item.oc};">
                            <i
                                class="fa-regular fa-solid fa-caret-right fa-1x"
                            />
                        </div>
                    {/if}
                </div>
            {/each}
        </div>
    </div>
{:else if page == 1}
    {#if sval == ""}
        <div class="wrapper">
            <div class="spinner" />

            <h3 class="u-t">results will be shown here</h3>
        </div>
    {:else}
        <div class="wrapper0">
            <div class="content" on:scroll={handleScroll} id="content">
                {#each returnedItems as item}
                    <div
                        class="container{item.type == 'premium'
                            ? '-premium'
                            : ''}"
                        id="UIDSCI-0000"
                    >
                        <div class="item-wrap">
                            <div
                                class="item{item.type == 'premium'
                                    ? '-premium'
                                    : ''}"
                            >
                                <div class="company">
                                    <h3 class="cn-text">{item.cc}</h3>
                                </div>
                                <div class="opp">
                                    <h3 class="opp-text">{item.opp}</h3>
                                </div>
                            </div>
                            {#if item.type == "premium"}
                                <div class="description">
                                    <h3 class="description-text">
                                        {item.description}
                                    </h3>
                                </div>
                            {/if}
                        </div>
                        {#if item.type == "premium"}
                            <div class="image-wrap">
                                <div class="im">
                                    <img
                                        class="image"
                                        src={item.url}
                                        alt="logo"
                                    />
                                </div>
                                <div class="forward" style="border: 0.8vw solid {item.oc};">
                                    <i
                                        class="fa-regular fa-solid fa-caret-right fa-1x"
                                    />
                                </div>
                            </div>
                        {:else}
                            <div class="im-normal">
                                <img class="image" src={item.url} alt="logo" />
                            </div>
                            <div class="forward-normal" style="border: 0.8vw solid {item.oc};">
                                <i
                                    class="fa-regular fa-solid fa-caret-right fa-1x"
                                />
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>
        </div>
    {/if}
{:else if page == 2}
    {#if !notifications}
        <div class="wrapper0">
            <div class="content" on:scroll={() => handleScroll()} id="content">
                {#each returnedItems as item}
                    <div
                        class="container{item.type == 'premium'
                            ? '-premium'
                            : ''}"
                        id="UIDSCI-0000"
                    >
                        <div class="item-wrap">
                            <div
                                class="item{item.type == 'premium'
                                    ? '-premium'
                                    : ''}"
                            >
                                <div class="company">
                                    <h3 class="cn-text">{item.cc}</h3>
                                </div>
                                <div class="opp">
                                    <h3 class="opp-text">{item.opp}</h3>
                                </div>
                            </div>
                            {#if item.type == "premium"}
                                <div class="description">
                                    <h3 class="description-text">
                                        {item.description}
                                    </h3>
                                </div>
                            {/if}
                        </div>
                        {#if item.type == "premium"}
                            <div class="image-wrap">
                                <div class="im">
                                    <img
                                        class="image"
                                        src={item.url}
                                        alt="logo"
                                    />
                                </div>
                                <div class="forward" style="border: 0.8vw solid {item.oc};">
                                    <i
                                        class="fa-regular fa-solid fa-caret-right fa-1x"
                                    />
                                </div>
                            </div>
                        {:else}
                            <div class="im-normal">
                                <img class="image" src={item.url} alt="logo" />
                            </div>
                            <div class="forward-normal" style="border: 0.8vw solid {item.oc};">
                                <i
                                    class="fa-regular fa-solid fa-caret-right fa-1x"
                                />
                            </div>
                        {/if}
                    </div>
                {/each}
            </div>
        </div>
    {:else}
        <div class="wrapper2">
            <h3 class="u-t">
                <a class="ut-a" href="">sign up</a> to see notifications
            </h3>
            <h3 class="u-ts">
                Please note that the full app is not released yet, so your
                account will be put on a waitlist. We're extremely sorry for the
                inconvenience caused, and thank you for understanding. <a
                    class="ut-a lp"
                    href="">learn more</a
                >
            </h3>
        </div>
    {/if}
{/if}

<style>
    @media (prefers-color-scheme: dark) {
        :root {
            --color: white;
            --cscheme: black;
            --searchurl: url("../search.png");
        }
    }

    @media (prefers-color-scheme: light) {
        :root {
            --color: black;
            --cscheme: white;
            --searchurl: url("../search_B.png");
        }
    }
    .spinner {
        display: flex;
        align-self: center;
        justify-self: center;
        width: 2rem;
        height: 2rem;
        margin: 4%;
        opacity: 0.55;

        background-image: var(--searchurl);
        background-size: 100% 100%;
        background-repeat: no-repeat;
        background-position: center;

        animation: rotates cubic-bezier(0.77, 0, 0.175, 1) infinite 2s;
    }

    @keyframes rotates {
        0% {
            rotate: 0deg;
        }
        100% {
            rotate: 360deg;
        }
    }

    .u-t {
        color: var(--uniColor);
        font-family: "Trebuchet MS", sans-serif;
        font-size: 4vw;
        opacity: 0.6;
    }

    .u-ts {
        color: var(--uniColor);
        font-family: "Trebuchet MS", sans-serif;
        font-size: 3vw;
        opacity: 0.55;

        width: 80%;
        text-align: center;

        margin-top: 2%;
    }

    .ut-a {
        color: #5533ebde;
        text-decoration: none;
    }

    .lp {
        color: #8e7ce1de;
    }

    .wrapper {
        width: 100%;
        height: 70vh;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
        margin-top: 5%;
        flex-direction: column;
    }

    .wrapper0 {
        width: 100%;
        height: 71vh;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
        margin-top: 15%;
    }

    .wrapper1 {
        width: 100%;
        height: 90vh;
        margin-top: 15%;
        display: flex;
        align-items: center;
        transition: ease-in-out 0.3s;
        justify-content: center;
    }

    .wrapper2 {
        width: 100%;
        height: 80%;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
        flex-direction: column;
    }

    .content {
        width: 94%;
        height: 98%;
        overflow-y: scroll;
        overflow-x: hidden;
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
        height: 5rem;
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: center;
        margin-bottom: 5%;
        align-items: center;

        border-left: 1vw solid rgb(113, 113, 113);
        box-sizing: border-box;
    }

    .container-premium {
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 8rem;
        width: 100%;
        display: flex;
        flex-direction: row;

        margin-bottom: 5%;

        border-left: 1vw solid rgb(125, 78, 78);
        box-sizing: border-box;
    }

    .im {
        width: 5rem;
        height: 5rem;
        position: relative;

        margin-bottom: auto;
    }

    .im-normal {
        width: 5rem;
        height: 5rem;

        margin-bottom: auto;
    }

    .image {
        width: 5rem;
        height: 5rem;
        border-radius: 1.5vw;
    }

    .image-wrap {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        width: 5rem;
        height: 8rem;
    }

    .forward {
        width: 100%;
        height: 2.5rem;
        margin: auto;
        border-radius: 1.5vw;
        border: 0.8vw solid #5533ebde;

        box-sizing: border-box;

        display: grid;
        place-items: center;
    }

    .forward-normal {
        height: 100%;
        width: 2.5rem;
        border-radius: 1.5vw;
        border: 0.8vw solid #5533ebde;

        box-sizing: border-box;

        display: grid;
        place-items: center;
        margin-left: 1%;
    }

    .item {
        box-sizing: border-box;
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 2.5rem;
        width: 80%;
    }

    .fa-caret-right {
        color: var(--color);
    }

    .item-premium {
        box-sizing: border-box;
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 2.5rem;
        width: 80%;
    }

    .company {
        width: 90%;
        height: 50%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 5%;
    }

    .cn-text {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 5vw;
        color: var(--color);
        opacity: 0.9;
    }

    .opp {
        width: 90%;
        height: 50%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 6%;
        margin-top: 2%;
    }

    .opp-text {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 4vw;
        color: var(--color);
        opacity: 0.75;
    }

    .description {
        width: 90%;
        height: 50%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        margin-left: 5%;
        margin-top: 5%;
        color: var(--color);
    }

    .description-text {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 3.2vw;
        color: var(--color);
        opacity: 0.6;
    }

    .item-wrap {
        width: 80%;
        height: 100%;
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
        background-color: transparent;
        border-radius: 10px;
    }

    /* scrollbar thumb */
    ::-webkit-scrollbar-thumb {
        background-color: #888;
        border-radius: 10px;
    }

    /* scrollbar corner */
    ::-webkit-scrollbar-corner {
        background-color: #f1f1f1;
    }

    /* scrollbar width and height */
    ::-webkit-scrollbar {
        width: 5px;
        height: 10px;
    }

    .fa-caret-right {
        color: var(--color);
    }
</style>
