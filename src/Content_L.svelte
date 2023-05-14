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
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: `red`,
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "green",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
    ];

    let results = [
        // turn into fetch
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: "coral",
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "gray",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "blue",
        },
    ];

    export const sUpdater = function sUpdater(data) {
        if (data != "" && page == 1) {
            sval = data;
            // client.js
            const searchString = "backend developer";

            async function get(url) {
                const response = await fetch(url);
                var data = await response.json();
                console.log(data);
                results = [];
                results.push(data);
                returnedItems = updateContent(results);
            }

            get("http://localhost:3000/api/");
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
        {#each items as item}
            <div class="container" id="UIDSCI-0000">
                <div class="im">
                    <img class="image" src={item.url} alt="logo" />
                </div>
                <div class="item" style="border: 0.35vw solid {item.oc};">
                    <div class="opp">
                        <h3 class="opp-text">{item.opp}</h3>
                    </div>
                    <div class="company">
                        <h3 class="cn-text">@{item.cc}</h3>
                    </div>
                </div>
                <div class="forward" style="border: 0.35vw solid {item.oc}">
                    <i class="fa-regular fa-solid fa-caret-right fa-2x" />
                </div>
            </div>
        {/each}
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
        width: 40%;
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
        width: 58%;
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
        width: 16%;
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
