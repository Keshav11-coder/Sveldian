<script>
    export let Value;
    export let index;

    const deviceWidth = window.innerWidth;

    let v2 = Value;

    function handleSheader() {
        v2 = !v2;
    }

    function onkeydown(event) {}
</script>

{#if deviceWidth < 1000}
    <div class="suggestion {Value ? '' : 'suggestion-da'}" id="sg">
        <div
            class="sheader {!v2 ? '' : 'sheader-ch'}"
            on:click={handleSheader}
            id="sh"
            on:keydown={onkeydown}
        >
            <div class="suggested"><h3 class="--suggested">Suggested</h3></div>
            <div class="caret">
                <i
                    class="fa-solid fa-caret-down fa-1x {!v2 ? '' : 'caret-up'}"
                    id="caret"
                />
            </div>
        </div>
        <div class="scontent {!v2 ? '' : 'shcontent'}" id="se" />
    </div>
{:else if (deviceWidth > 1000 && index == 3) || index == 4}
    <div class="suggestion-2 {!Value ? '' : 'suggestion-da'}" id="sg">
        <div
            class="sheader {!v2 ? '' : 'sheader-ch'}"
            id="sh"
            on:click={handleSheader}
            on:keydown={onkeydown}
        >
            <div class="suggested"><h3 class="--suggested">Suggested</h3></div>
            <div class="caret">
                <i
                    class="fa-solid fa-caret-down fa-1x {!v2 ? '' : 'caret-up'}"
                    id="caret"
                />
            </div>
        </div>
        <div class="scontent {!v2 ? '' : 'shcontent'}" id="se" />
    </div>
{/if}

<style>
    .suggestion {
        width: 40%;
        height: 70%;
        transition: ease-in-out 0.4s;
        /*border: 3px solid var(--SdPurpleAlt);*/
        border-radius: 6px;
        align-self: center;
        justify-self: center;
        position: relative;
        margin-top: 8%;
        flex-direction: column;
        display: flex;
        opacity: 1;
        cursor: pointer;
    }

    .suggestion-2 {
        width: 35%;
        height: 70%;
        transition: ease-in-out 0.4s;
        /*border: 3px solid var(--SdPurpleAlt);*/
        border-radius: 6px;
        align-self: center;
        justify-self: center;
        position: relative;
        margin-top: 8%;
        flex-direction: column;
        display: flex;
        opacity: 1;
        cursor: pointer;
    }

    .suggestion-da {
        opacity: 0;
        z-index: -5;
    }

    .sheader {
        width: 100%;
        height: 15%;
        display: grid;
        grid-template-columns: 80% 20%;
        border: 3px solid var(--SdPurpleAlt);
        border-radius: 10px 10px;

        transition: ease-in-out 0.4s;
    }

    .sheader-ch {
        border-radius: 10px 10px 0px 0px;
        transition: ease-in-out 0.4s;
    }

    .suggested {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    .--suggested {
        font-family: "Montserrat Alternates", sans-serif;
        font-size: 0.7vw;
        color: var(--placeHC);
        margin-left: 6%;
    }

    .caret {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        color: var(--placeHC);
    }

    .fa-caret-down {
        text-decoration: none;
        transition: ease-in-out 0.4s;
    }

    .caret-up {
        transform: rotate(180deg);
    }

    .scontent {
        height: 1%;
        width: 100%;
        transition: ease-in-out 0.3s;
    }

    .shcontent {
        width: 100%;
        height: 85%;
        border-top: none;
        border-right: 3px solid var(--SdPurpleAlt);
        border-bottom: 3px solid var(--SdPurpleAlt);
        border-left: 3px solid var(--SdPurpleAlt);
        border-radius: 0px 0px 10px 10px;
    }

    @media only screen and (min-width: 1000px) {
        .suggestion {
            margin-bottom: 3%;
            margin-top: 3%;
        }

        .suggestion-2 {
            margin-bottom: 3%;
            margin-top: 3%;
        }
    }
</style>
