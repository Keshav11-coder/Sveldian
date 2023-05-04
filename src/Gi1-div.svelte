<script>
    export let gi;
    export let activator = false;
    export let activatorValue = 0;

    var input1Error = false;
    let inputValue1 = "";
    const deviceWidth = window.innerWidth;

    export const check1i = function check1i() {
        if (inputValue1 == "") {
            input1Error = true;
            console.log(`string 1 ${input1Error}`);
        } else {
            input1Error = false;
            input1Error = false;
            console.log(`string 1 ${input1Error}`);
        }
        return input1Error;
    };

    function handleInput(event) {
        inputValue1 = event.target.value;
    }

    function changeActivator(newV) {
        if (activator == true) {
            activatorValue = newV;
        }
    }

    $: {
        if (deviceWidth < 1000) {
            if (activatorValue == 1) {
                if (gi == "click here") {
                    gi = "minimum 30 words";
                }
            } else if (activatorValue == 0) {
                if (gi == "minimum 30 words") {
                    gi = "click here";
                }
            } else {
            }
        }
    }
</script>

{#if deviceWidth < 1000}
    <div class="gi-div" id="border-ray-div">
        <textarea
            on:click={() => changeActivator(1)}
            class="ginput-1 {!activatorValue ? '' : 'ginput-2'}"
            placeholder={gi}
            id="i"
            on:input={handleInput}
            style={input1Error && activatorValue == 0
                ? "border: var(--borderSize) solid red;"
                : input1Error && activatorValue == 1
                ? "border-bottom: var(--borderSize) solid red; border-top:none;border-left:none;border-right:none; border-radius:0;"
                : ""}
        />
    </div>
{:else if deviceWidth > 1000}
    <div
        class="{gi == 'minimum 30 words' ? 'gi-divl' : 'gi-div'}"
        id="border-ray-div"
    >
        {#if gi == "minimum 30 words"}
            <textarea
                class="ginput-1 {!activatorValue ? '' : 'ginput-2'}"
                placeholder={gi}
                id="i"
                on:input={handleInput}
                style={input1Error && activatorValue == 0
                    ? "border: var(--borderSize) solid red;"
                    : input1Error && activatorValue == 1
                    ? "border-bottom: var(--borderSize) solid red; border-top:none;border-left:none;border-right:none; border-radius:0;"
                    : ""}
            />
        {:else if gi != "minimum 30 words"}
            <input
                type="text"
                class="ginput-1 {!activatorValue ? '' : 'ginput-2'}"
                placeholder={gi}
                id="i"
                on:input={handleInput}
                style={input1Error && activatorValue == 0
                    ? "border: var(--borderSize) solid red;"
                    : input1Error && activatorValue == 1
                    ? "border-bottom: var(--borderSize) solid red; border-top:none;border-left:none;border-right:none; border-radius:0;"
                    : ""}
            />
        {/if}
    </div>
{/if}

<style>
    @media (prefers-color-scheme: light) {
        :root {
            --ginColor: transparent;
            --borderSize: 0.15vw;
            --SdPurpleAlt: #5533ebde;
            --placeHC: black;
        }
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --ginColor: transparent;
            --borderSize: 0.15vw;
            --SdPurpleAlt: #5533ebde;
            --placeHC: white;
        }
    }

    .gi-div {
        transition: transform 1s ease-in-out;
        width: 75%;
        height: 15%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        align-self: center;
        border-radius: 6px;
        z-index: 9;
        margin-top: 3%;
    }

    .ginput-1 {
        transition: ease-in-out 0.4s;
        border-style: none;
        outline: none;
        width: 100%;
        height: 100%;
        font-family: "Trebuchet MS", sans-serif;
        font-size: 5vw;
        padding-left: 5%;
        padding-right: 5%;
        border-radius: 8px;

        margin-top: 2%;

        background-color: var(--ginColor);

        border: var(--borderSize) solid var(--SdPurpleAlt);

        color: var(--placeHC);

        padding-top: 2.5vh;
        padding-bottom: auto;
    }

    .ginput-2 {
        border-radius: 0px;

        border-style: none;
        outline: none;

        border-bottom: var(--borderSize) solid var(--SdPurpleAlt);
    }

    textarea::-webkit-scrollbar {
        display: none;
    }
    textarea {
        overflow-y: scroll;
        -webkit-overflow-scrolling: touch;
    }

    @media only screen and (min-width: 1000px) {
        /* For desktop: */
        .gi-divl {
            transition: transform 1s ease-in-out;
            width: 40%;
            height: 35%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            align-self: center;
            border-radius: 6px;
        }

        .gi-div {
            transition: transform 1s ease-in-out;
            width: 30%;
            height: 18%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            align-self: center;
            border-radius: 6px;
        }

        .ginput-1 {
            transition: ease-in-out 0.4s;
            border-style: none;
            outline: none;
            width: 100%;
            height: 100%;
            font-family: "Trebuchet MS", sans-serif;
            font-size: 0.8vw;
            padding-left: 5%;
            padding-right: 5%;
            border-radius: 8px;

            margin-top: 2%;
            padding-bottom: 2.5vh;

            background-color: var(--ginColor);

            border: var(--borderSize) solid var(--SdPurpleAlt);

            color: var(--placeHC);
        }

        ::placeholder {
            font-size: 0.8vw;
            color: var(--placeHC);
            opacity: 0.7;
            display: flex;
        }
    }
</style>
