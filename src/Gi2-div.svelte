<script>
    export let gi1;
    export let gi2;

    export let gi1t;
    export let gi2t;

    export let gi1max;
    export let gi2max;

    export let skip = false;

    var input1Error = false;
    var input2Error = false;
    let inputValue1 = "";
    let inputValue2 = "";
    export const check2i = function check2i() {
        if (inputValue1 == "") {
            input1Error = true;
            console.log(`string 1 ${input1Error}`);
            console.log(`string 2 ${input2Error}`);
        } else {
            input1Error = false;
        }
        if (inputValue2 == "") {
            input2Error = true;
            console.log(`string 1 ${input1Error}`);
            console.log(`string 2 ${input2Error}`);
        } else {
            input2Error = false;
        }
        if (inputValue1 != "" && inputValue2 != "") {
            input1Error = false;
            input2Error = false;
            console.log(`string 1 ${input1Error}`);
            console.log(`string 2 ${input2Error}`);
        }
        return [input1Error, input2Error];
    };

    function handleInput1(event) {
        inputValue1 = event.target.value;
    }

    function handleInput2(event) {
        inputValue2 = event.target.value;
    }

    const deviceWidth = window.innerWidth;
</script>

{#if deviceWidth < 1000}
    <div class={skip ? "gi21-div" : "gi2-div"} id="border-ray-div">
        <input
            type={gi1t}
            class="ginput-1 {input1Error ? 'ginput-err' : ''}"
            maxlength={gi1max}
            placeholder={gi1}
            on:input={handleInput1}
            id="1"
        />
        <input
            type={gi2t}
            class="ginput-1 {input2Error ? 'ginput-err' : ''}"
            maxlength={gi2max}
            placeholder={gi2}
            on:input={handleInput2}
            id="2"
        />
    </div>
{:else if deviceWidth > 1000}
    <div class={skip ? "gi21-div" : "gi2-div"} id="border-ray-div">
        <input
            type={gi1t}
            class="ginput-1"
            maxlength={gi1max}
            placeholder={gi1}
            on:input={handleInput1}
            id="1"
            style="{input1Error ? 'border: var(--borderSize) solid red;' : ''}"
        />
        <input
            type={gi2t}
            class="ginput-1 {input2Error ? 'ginput-err' : ''}"
            maxlength={gi2max}
            placeholder={gi2}
            on:input={handleInput2}
            id="2"
            style="{input1Error ? 'border: var(--borderSize) solid red;' : ''}"
        />
    </div>
{/if}

<style>
    @media (prefers-color-scheme: light) {
        :root {
            --ginColor: transparent;
            --borderSize: 3px;
            --SdPurpleAlt: #5533ebde;
            --placeHC: black;
        }
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --ginColor: transparent;
            --borderSize: 3px;
            --SdPurpleAlt: #5533ebde;
            --placeHC: white;
        }
    }

    .gi2-div {
        transition: transform 1s ease-in-out;
        width: 75%;
        height: 30%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        align-self: center;
        border-radius: 6px;
    }

    .gi21-div {
        transition: transform 1s ease-in-out;
        width: 75%;
        height: 30%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        align-self: center;
        border-radius: 6px;
    }

    .ginput-1 {
        transition: ease-in-out 0.2s;
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
    }

    .ginput-err {
        border: var(--borderSize) solid red;
    }

    ::placeholder {
        font-size: 4.8vw;
        color: var(--placeHC);
        opacity: 0.7;
    }

    input[type="number"]::-webkit-inner-spin-button,
    input[type="number"]::-webkit-outer-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    @media only screen and (min-width: 1000px) {
        /* For desktop: */
        .gi2-div {
            transition: transform 1s ease-in-out;
            width: 30%;
            height: 30%;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            align-self: center;
            border-radius: 6px;
        }

        .gi21-div {
            transition: transform 1s ease-in-out;
            width: 30%;
            height: 40%;
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
