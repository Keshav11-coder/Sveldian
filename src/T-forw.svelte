<script>
    import App from "./App.svelte";

    export let includeSkip = false;

    export let variableToUpdate;

    const updateVariable = (content) => {
        variableToUpdate = content;
    };

    function loadq() {
        updateVariable("TEST NEW BUTTON");
        console.log("loadq, triggered");
    }

    let content;

    let sW;

    if (includeSkip == true) {
        sW = "t-forw2";
        content = `
            <div class="forw btn">
                <h3 class="bl">next</h3>
            </div>
            <div class="skip btn">
                <h3 class="ppl">skip</h3>
            </div>
        `;
    } else if (includeSkip == false) {
        sW = "t-forw";
        content = '<div class="btn"><h3 class="bl">next</h3></div>';
    } else {

    }
</script>

<div class={sW} id="tf">
    {@html content}
</div>

<style>
    
</style>
