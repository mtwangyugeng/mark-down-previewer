<script>
import Edits from "./Edits.svelte";
import FileName from "./FileName.svelte";

import Files from "./Files.svelte";
import Menu from "./Menu.svelte";

</script>
<section>
    <span>
        <Files />
        <Edits />
    </span>
    <span>
        <FileName />
        <Menu />
    </span>
</section>


<style>
    section {
        background-color: orange;
        height: 40px;
        display: flex;
        justify-content: space-between;
    }
</style>