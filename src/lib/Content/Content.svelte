<script>
import { placeholder } from "./Constants";

import LeftPanel from "./LeftPanel.svelte";
import Resizer from "./Resizer.svelte";
import RightPanel from "./RightPanel.svelte";

let imp = placeholder;

// const readyChannel = new BroadcastChannel('ready_channel');
// readyChannel.postMessage('ready');
// readyChannel.addEventListener("message", e => {
//   if(e.data === 'ready') {
//     workChannel.postMessage(imp);
//   }
// });
const saved = localStorage.getItem('markdown')
if (saved != null) imp = saved

const workChannel = new BroadcastChannel('work_channel');

workChannel.addEventListener("message", e => {
  imp = e.data;
});

const handleInput = (e) => {
    imp = e.target.value;
    workChannel.postMessage(imp);
    localStorage.setItem("markdown", imp)
}


</script>


<section>
    <LeftPanel imp={imp} on:input={handleInput}/>
    <Resizer />
    <RightPanel imp={imp}/>
</section>

<style>
    section {
        flex: 1;
        background-color: pink;
        display: flex;
    }
</style>