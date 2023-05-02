<script>
    /*
    
    credit to chatGPT for this spinner
    
    */
   
    export let isLoading = false;
</script>

{#if isLoading}
    <div class="loading-spinner">
        <div />
        <div />
        <div />
        <div />
    </div>
{/if}

<style>
    .loading-spinner {
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 9999;
        background-color: rgba(0, 0, 0, 0.5);
    }

    .full-screen {
        height: 100vh;
    }

    .loading-spinner div {
        width: 18px;
        height: 18px;
        border-radius: 50%;
        background-color: white;
        animation: loading-spinner 1.4s infinite ease-in-out both;
        margin-right: 4px;
    }

    .loading-spinner div:nth-child(1) {
        animation-delay: -0.32s;
    }

    .loading-spinner div:nth-child(2) {
        animation-delay: -0.16s;
    }

    .loading-spinner div:nth-child(3) {
        animation-delay: 0;
    }

    .loading-spinner div:nth-child(4) {
        animation-delay: 0.16s;
    }

    @keyframes loading-spinner {
        0% {
            transform: scale(0);
        }
        100% {
            transform: scale(1);
            opacity: 0;
        }
    }
</style>
