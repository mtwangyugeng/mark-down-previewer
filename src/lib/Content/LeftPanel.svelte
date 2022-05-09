<script>
    export let imp;

</script>


<section>
    <textarea value={imp} on:input/>
</section>


<style>
    section {
        height: 100%;
        width: 50%;
    }
    textarea {
        resize: none;
        height: 100%;
        width: 100%;
    }
</style>