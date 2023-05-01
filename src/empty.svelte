<script>
    let prevScrollPos = window.pageYOffset;
    export let topNavVisible = true;
    let timeoutId;

    /*function handleScroll(event) {
        let currentScrollPos = event.target.scrollTop;
        if (prevScrollPos > currentScrollPos) {
            topNavVisible = true; // user is scrolling up, show the top nav
        } else {
            topNavVisible = false; // user is scrolling down, hide the top nav
        }
        prevScrollPos = currentScrollPos;
    }*/

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
</script>

<div class="wrapper0 {topNavVisible ? '' : 'wrapper1'}">
    <div class="content" on:scroll={handleScroll}>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
            <div class="c1">
                <div class="image"><img src="./fb.png" alt="" /></div>
            </div>
            <div class="c2">
                <div class="oppTitle"></div>
                <div class="c3"></div>
            </div>
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
        <div class="item" id="UIDSCI-0000">
            <!--Unique ID Skilldian Content Item - * * * *-->
        </div>
    </div>
</div>

<style>
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

    .item {
        background-color: rgb(173, 141, 141);
        animation: fadeInUp 0.3s ease-in-out forwards;
        height: 20%;
        width: 100%;
        border-radius: 10px;
        display: flex;
        margin-bottom: 3%;
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
