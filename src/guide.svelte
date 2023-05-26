<!--this is a random positioned component, that means it can be moved around, and is not a fixed height element !(width: 100%), instead using pixels AND / OR rem-->

<script>
    export let index;
</script>

<div class="guide">
    <div class="title"><h3 class="--title">Lorem Ipsum</h3></div>
    <div class="content">
        <h3 class="--content">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur
            vitae lorem consectetur, rhoncus orci ornare, laoreet dui.
        </h3>
    </div>
    <div class="image-box">
        <div class="img-color">
            <img class="img" src="../random-light.png">
        </div>
    </div>
</div>

<style>
    .guide{
        width: 10rem;
        height: 20rem;
        border-radius: 0 0.8vw 0.8vw 0;
        background-color: rgba(255, 255, 255, 0.677);
        position: absolute;
        top:50%;
        left:0;
        padding: 9px;
    }

    .title{
        width: 100%;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 1vw;
        margin-bottom: 3%;
        height: 7%;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: row;
    }

    .content{
        width: 100%;
        height: 45%;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        font-size: 0.8vw;
        overflow-y: scroll;
        padding: 2px;
        box-sizing:content-box;
        display: flex;
        align-items: flex-start;
        justify-content: flex-start;
    }

    ::-webkit-scrollbar{
        display:none;
    }

    .image-box{
        width: 100%;
        height: 45%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .img-color{
        width: 3.5rem;
        height: 3.5rem;
        background-color: #5533ebde;
        border-radius: 6px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .img{
        width: 2.5rem;
        height: 1.5rem;
        max-width: 2.5rem;
    }
</style>
