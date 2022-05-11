<script>
let dragging = false;
let ogX = null;
export let updateLeftPanelWidth;

const initiate = (e) => {
    dragging = true;
    ogX = e.clientX;
}

const move = (e) => {
    if(dragging)
        ogX = updateLeftPanelWidth(e.clientX - ogX);
}

const release = () => {
    dragging = false;
}

</script>

<svelte:window on:mousemove={move} on:mouseup={release} />

<section on:mousedown={initiate}>

</section>

<style>
    section {
        width: 10px;
        background-color: #000;
    }
</style>