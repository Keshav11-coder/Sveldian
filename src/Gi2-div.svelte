<script>
    export let gi1;
    export let gi2;

    export let gi1t;
    export let gi2t;

    export let gi1max;
    export let gi2max;

    export let skip = false;

    export const check2i = function check2i(string1, string2){
        if(string1 != '' && string2 != ''){
            
        }
        console.log("string empty")
    }
</script>

<div class={skip ? "gi21-div" : "gi2-div"} id="border-ray-div">
    <input
        type={gi1t}
        class="ginput-1"
        maxlength={gi1max}
        placeholder={gi1}
        id="i"
    />
    <input
        type={gi2t}
        class="ginput-1"
        maxlength={gi2max}
        placeholder={gi2}
        id="i"
    />
</div>

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
