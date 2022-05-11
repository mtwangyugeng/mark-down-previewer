<script>
export let imp;
// 
import MarkdownIt from 'markdown-it';
const md = new MarkdownIt();
$: converted = md.render(imp)
</script>

<section>
    {@html converted}
</section>


<style>
    section {
        flex: 1;
        overflow: auto;
    }
</style>