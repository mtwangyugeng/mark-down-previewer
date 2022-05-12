<script>
import { onMount } from "svelte";

import { placeholder } from "./Constants";

import LeftPanel from "./LeftPanel.svelte";
import Resizer from "./Resizer.svelte";
import RightPanel from "./RightPanel.svelte";


let imp = "placeholder";

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

let leftPanelWidth = 0;
let leftPanelProportion = 0.5;
const updateLeftPanelWidth = (imp) => {
    leftPanelWidth += imp
    leftPanelProportion = leftPanelWidth / container.offsetWidth;
    return leftPanelWidth;
}

let container;
onMount (()=>{
    changeLeftPanelWidth();
})

const changeLeftPanelWidth = () => {
    leftPanelWidth = container.offsetWidth * leftPanelProportion;
}

</script>

<svelte:window on:resize={changeLeftPanelWidth} />

<section bind:this={container}>
    <LeftPanel imp={imp} on:input={handleInput} leftPanelWidth={leftPanelWidth} />
    <Resizer {updateLeftPanelWidth} />
    <RightPanel imp={imp}/>
</section>

<style>
    section {
        flex: 1;
        background-color: pink;
        display: flex;
    }
</style>