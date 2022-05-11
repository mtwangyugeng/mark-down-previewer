<script>
    export let imp;
    export let leftPanelWidth;
</script>


<section style = "width: {leftPanelWidth}px;" >
    <textarea value={imp} on:input/>
</section>


<style>
    section {
        height: 100%;
    }
    textarea {
        resize: none;
        height: 100%;
        width: 100%;
    }
</style>