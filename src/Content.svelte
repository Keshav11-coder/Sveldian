<script>
    let prevScrollPos = window.pageYOffset;
    let timeoutId;
    function keyDown(event) {}
    let sval = "";
    let returnedItems = []; //NOTE: THIS VARIABLE IS TEMPORARY. there will be replacements placed in the future, meaning this is NOT the official solution

    export let topNavVisible = true;
    export let xtend;

    export const callSearchClear = function callSearchClear (){
        sval = "";
    }

    let items = [
        // turn into fetch
        {
            url: "../fb.png",
            opp: "Web Developer",
            cc: "FaceBook",
            oc: "white",
        },
        {
            url: "../fb.png",
            opp: "Database manager",
            cc: "FaceBook",
            oc: "blue",
        },
        {
            url: "../fb.png",
            opp: "Backend Developer",
            cc: "FaceBook",
            oc: "red",
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
        if (data != "" && xtend == true) {
            sval = data;
            returnedItems = updateContent(results);
        }
    };

    function handleScroll(event) {
        let currentScrollPos = event.target.scrollTop;
        if (prevScrollPos > currentScrollPos) {
            if (!topNavVisible) {
                clearTimeout(timeoutId);
                topNavVisible = true;
            }
        } else {
            if (topNavVisible) {
                timeoutId = setTimeout(() => {
                    topNavVisible = false;
                }, 250); // adjust the delay time as needed
            }
        }
        prevScrollPos = currentScrollPos;
    }

    function updateContent(items) {
        items = [...items];
        return items;
    }
</script>

{#if !xtend}
    <div class="wrapper0 {topNavVisible ? '' : 'wrapper1'}">
        <div class="content" on:scroll={() => handleScroll()} id="content">
            {#each items as item}
                <div class="container" id="UIDSCI-0000">
                    <!--Unique ID Skilldian Content Item - * * * *-->
                    <div class="im"><img class="image" src={item.url} alt="logo" /></div>
                    <div class="item" style="border: 0.7vw solid {item.oc};">
                        <div
                            class="role-r2"
                            style="border-bottom: 0.7vw solid {item.oc};"
                        >
                            <h3 class="--item-t1">{item.opp}</h3>
                        </div>
                        <div class="b-r2">
                            <div
                                class="c b-r2-i2"
                                style="border-right: 0.35vw solid {item.oc};"
                            >
                                <h3 class="--item-t1">@{item.cc}</h3>
                            </div>
                            <div
                                class="n-rr b-r2-i2"
                                style="border-left: 0.35vw solid {item.oc};"
                            >
                                <i
                                    class="fa-regular fa-solid fa-caret-right fa-2x"
                                />
                            </div>
                        </div>
                    </div>
                </div>
            {/each}
        </div>
    </div>
{:else if xtend}
    {#if sval == ""}
        <div class="wrapper0">
            <h3 class="u-t">results will be shown here</h3>
        </div>
    {:else}
        <div class="wrapper0">
            <div class="content" on:scroll={() => handleScroll()} id="content">
                {#each returnedItems as item}
                    <div class="container" id="UIDSCI-0000">
                        <!--Unique ID Skilldian Content Item - * * * *-->
                        <div class="im">
                            <img class="image" src={item.url} alt="logo" />
                        </div>
                        <div
                            class="item"
                            style="border: 0.7vw solid {item.oc};"
                        >
                            <div
                                class="role-r2"
                                style="border-bottom: 0.7vw solid {item.oc};"
                            >
                                <h3 class="--item-t1">{item.opp}</h3>
                            </div>
                            <div class="b-r2">
                                <div
                                    class="c b-r2-i2"
                                    style="border-right: 0.35vw solid {item.oc};"
                                >
                                    <h3 class="--item-t1">@{item.cc}</h3>
                                </div>
                                <div
                                    class="n-rr b-r2-i2"
                                    style="border-left: 0.35vw solid {item.oc};"
                                >
                                    <i
                                        class="fa-regular fa-solid fa-caret-right fa-2x"
                                    />
                                </div>
                            </div>
                        </div>
                    </div>
                {/each}
            </div>
        </div>
    {/if}
{/if}

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

    .u-t {
        color: var(--uniColor);
        font-family: "Trebuchet MS", sans-serif;
        font-size: 4vw;
        opacity: 0.6;
    }

    .wrapper0 {
        width: 100%;
        height: 80%;
        position: inherit;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: ease-in-out 0.3s;
    }

    .wrapper1 {
        width: 100%;
        height: 93%;
        position: inherit;
        display: flex;
        align-items: center;
        transition: ease-in-out 0.3s;
        justify-content: center;
    }

    .content {
        width: 94%;
        height: 98%;
        grid-gap: 25px;
        overflow-y: scroll;
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
        height: 20%;
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        margin-bottom: 3%;
    }

    .im {
        width: 30%;
        padding-bottom: 0%;
        position: relative;

        border-radius: 12px 0px 0px 12px;

        margin-top: auto;
        margin-bottom: auto;
    }

    .image {
        width: 100%;
        border-radius: 3vw 0px 0px 3vw;
    }

    .item {
        border: 0.7vw solid #3b5998;
        border-radius: 1.2vw 3vw 3vw 1.2vw;
        box-sizing: border-box;
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 100%;
        width: 70%;
        /*box-shadow: -6px 0px 35px 0px rgba(0, 0, 0, 0.75);*/
    }

    .role-r2 {
        width: 100%;
        height: 50%;
        border-radius: 1.2vw 3vw 0 0;
        display: flex;
        align-items: center;
        justify-content: center;
        border-bottom: 0.7vw solid #3b5998;
        box-sizing: border-box;
    }

    .b-r2 {
        width: 100%;
        height: 50%;
        border-radius: 0 0 3vw 1.2vw;
        display: flex;
        flex-direction: row;
    }

    .b-r2-i2 {
        width: 50%;
        height: 100%;
    }

    .c {
        display: flex;
        align-items: center;
        justify-content: center;
        border-right: 0.35vw solid #3b5998;
        box-sizing: border-box;
    }

    .n-rr {
        display: flex;
        align-items: center;
        justify-content: center;
        border-left: 0.35vw solid #3b5998;
        box-sizing: border-box;
    }

    .--item-t1 {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 4.6vw;
        color: var(--color);
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
</style>
