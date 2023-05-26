<script>
    let menus = false;
    export let topNavVisible = false;

    function menuState(menuVal) {
        menus = menuVal;
    }

    function handleKd(event) {}
</script>

<div class="menu {topNavVisible ? '' : 'menu-hide'}">
    <div class="logo">
        <div class="logo-img"><img src="../s.svg" alt="" class="limg" /></div>
        <h3 class="Title">Skilldian</h3>
    </div>
    <div
        class="menu-b {menus ? 'menu-a' : ''}"
        on:click={() => menuState(true)}
        on:keydown={handleKd}
    >
        {#if menus}
            <div class="m-item reload-c" />
            <div class="m-item notifications-c" />
            <div class="m-item signup-c">sign up</div>
            <div
                class="m-item close"
                on:click={(event) => { event.stopPropagation(); menuState(false); }}
                on:keydown={handleKd}
            />
        {:else if !menus}
            <img src="../bars-light.png" alt="" class="mimg" />
        {/if}
    </div>
</div>

<style>
    .menu {
        width: 98vw;
        height: 3.5rem;
        display: flex;
        position: relative;
        margin-top: 2vh;
        margin-right: auto;
        margin-left: auto;
        user-select: none;
        margin-left: 2vh;
        transition: ease-in-out 0.4s;
    }

    .menu-hide {
        position: absolute;
        transition: ease-in-out 0.4s;
    }

    .logo {
        width: 18%;
        height: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;
    }

    .logo-img {
        width: 3.5rem;
        height: 3.5rem;
        display: flex;
        margin-right: 3%;
    }

    .limg {
        width: 100%;
        height: 100%;
        border-radius: 6px;
        object-fit: cover;
    }

    .Title {
        font-family: "Trebuchet MS", sans-serif;
        font-size: 1.2vw;
        color: white;
        text-decoration: none;
    }

    .menu-b {
        width: 3.5rem;
        height: 3.5rem;
        display: flex;
        background: #5533ebde;
        position: absolute;
        margin-right: 2vh;
        right: 0;
        border-radius: 6px;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: ease-in-out 0.2s;
    }

    .menu-a {
        height: 14rem;
        transition: ease-in-out 0.2s;
        cursor: default;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
    }

    .mimg {
        width: 60%;
        height: 60%;
    }

    .m-item {
        width: 3rem;
        height: 3rem;
        background-color: #000000de;
        margin-bottom: 7%;
        border-radius: 0.3vw;
    }

    .m-item:hover{
        cursor: pointer;
    }

    .reload-c {
        background-image: url("../reload.png");
        background-size: 45% 45%;
        background-repeat: no-repeat;
        background-position: center;
    }

    .notifications-c {
        background-image: url("../bell.png");
        background-size: 45% 45%;
        background-repeat: no-repeat;
        background-position: center;
    }

    .signup-c {
        display: flex;
        align-items: center;
        justify-content: center;
        font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
            "Lucida Sans", Arial, sans-serif;
        font-size: 1.3vw;
        color: var(--color);
        text-align: center;
    }

    .close {
        background-image: url("../x.png");
        background-size: 45% 45%;
        background-repeat: no-repeat;
        background-position: center;
        z-index: 6;
    }
</style>
