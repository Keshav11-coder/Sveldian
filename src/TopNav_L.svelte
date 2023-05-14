<script>
    export let topNavVisible

    let react_sb = false;

    function handleKd(event) {}

    function s_react(new_) {
        react_sb = new_;
    }
</script>

<div class="snav {!topNavVisible ? 'snav-hide' : ''}">
    <div class="sButton {react_sb ? 'sb_react r' : ''}">
        <img class="rimg" src="../random-light.png" alt="" />
    </div>
    <div class="search-i" on:click={() => s_react(true)} on:keydown={handleKd}>
        <input class="dinput" placeholder="search ..." />
    </div>
    <div class="sButton {react_sb ? 'sb_react s' : ''}">
        <img class="simg" src="../search.png" alt="" />
    </div>
</div>

<style>
    .snav {
        width: 100%;
        height: 10%;
        margin-top: 3%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: row;
        transition: ease-in-out 0.4s;
    }

    .snav-hide{
        margin-top: 0%;
        transition: ease-in-out 0.4s;
    }

    .sButton {
        width: 4rem;
        height: 4rem;
        background-color: #5533ebde;
        border-radius: 6px;
        transition: ease-in-out 0.4s;
        margin-left: -3.5%;
        margin-right: -3.5%;
        z-index: -3;
        opacity: 0;
    }

    .search-i {
        height: 4rem;
        width: 40%;
        border-radius: 6px;
        transition: ease-in-out 0.4s;

        border: 0.2vw solid #5533ebde;

        box-sizing: border-box;
    }

    .sb_react {
        transition: ease-in-out 0.4s;
        margin-left: 0.5%;
        margin-right: 0.5%;
        z-index: -3;
        opacity: 1;
    }

    .dinput {
        width: 100%;
        height: 100%;
        font-family: "Trebuchet MS", sans-serif;
        font-size: 1vw;
        border-radius: 6px;
        outline: none;
        border-style: none;
        padding-left: 5%;
        box-sizing: border-box;

        background:transparent;
        color: white;
    }

    ::placeholder {
        font-size: 1vw;
        color :white;
        opacity: .55;
        font-family: "Trebuchet MS", sans-serif;
    }

    .r {
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 0;
    }

    .rimg {
        width: 3rem;
        height: 2rem;
    }

    .s {
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 0;
    }

    .simg {
        width: 2rem;
        height: 2rem;
    }

    .r:hover,.s:hover{
        cursor: pointer;
    }
</style>
