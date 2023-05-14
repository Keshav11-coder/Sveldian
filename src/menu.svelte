<script>
    let menus = false;
    export let topNavVisible = false;

    function menuState(menuVal){
        menus = menuVal;
    }

    function handleKd(event){}
</script>

<div class="menu {topNavVisible ? '' : 'menu-hide'}">
    <div class="logo">
        <div class="logo-img"><img src="../s.svg" alt="" class="limg" /></div>
        <h3 class="Title">
            Skilldian
        </h3>
    </div>
    <div class="menu-b {menus ? 'menu-a':''}" on:click={() => menuState(true)} on:keydown={handleKd}>
        {#if menus}
        {:else if !menus}
        <img src="../bars-light.png" alt="" class="mimg">
        {/if}
    </div>
</div>

<style>
    .menu {
        width: 98vw;
        height: 3.5rem;
        display: flex;
        position:relative;
        margin-top: 2vh;
        margin-right: auto;
        margin-left: auto;
        user-select: none;
        margin-left: 2vh;
        transition: ease-in-out 0.4s;
    }

    .menu-hide{
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

    .limg{
        width: 100%;
        height: 100%;
        border-radius: 6px;
        object-fit: cover;
    }

    .Title{
        font-family:'Trebuchet MS', sans-serif;
        font-size: 1.2vw;
        color: white;
        text-decoration: none;
    }

    .menu-b{
        width: 3.5rem;
        height: 3.5rem;
        background: #5533ebde;
        display: flex;
        position: absolute;
        margin-right: 2vh;
        right: 0;
        border-radius: 6px;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: ease-in-out 0.2s;
    }

    .menu-a{
        height: 18.5rem;
        transition: ease-in-out 0.2s;
        cursor:default;
    }

    .mimg{
        width: 60%;
        height: 60%;
    }
</style>
