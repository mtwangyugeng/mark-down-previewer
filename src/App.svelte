<script>

  let imp = "";
  let neo = "";

  const readyChannel = new BroadcastChannel('ready_channel');
  readyChannel.postMessage('ready');
  readyChannel.addEventListener("message", e => {
    if(e.data === 'ready') {
      workChannel.postMessage(imp);
    }
  });

  const workChannel = new BroadcastChannel('work_channel');

  workChannel.addEventListener("message", e => {
    neo = e.data;
  });

  $: workChannel.postMessage(imp);

  
</script>

<main>
  {neo}
  <input bind:value={imp}/>
  {imp}
</main>

<style>

</style>
