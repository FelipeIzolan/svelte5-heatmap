<script lang="ts">
  import "../global.css";
  import Heatmap from "$lib/Heatmap.svelte";

  let colors;
  // colors = ["#0D41E1", "#0C63E7", "#0A85ED", "#09A6F3", "#07C8F9"];

  let data = $state<{ [key: string]: number }>({});
  let year = $state(2025);

  function fillMap() {
    let map: { [key: string]: number } = {};
    let max = Math.round(Math.random() * 24) + 8;
    for (let m = 0; m <= 12; m++) {
      for (let d = 0; d <= 31; d++) {
        let key = `${year}-${("0" + m).slice(-2)}-${("0" + d).slice(-2)}`;
        map[key] = Math.round(Math.random() * max);
      }
    }
    data = map;
  }

  fillMap();
</script>

<svelte:head>
  <title>Heatmap.svelte</title>
</svelte:head>

<div
  style="display:flex;gap:0.5em;justify-content:center;align-items:center;margin:2em 0"
>
  <img
    src="https://svelte.dev/favicon.png"
    alt="svelte logo"
    width="32"
    height="32"
  />
  <h1>Heatmap.svelte</h1>
</div>
<div style="font-size:12px">
  <Heatmap
    {data}
    {year}
    {colors}
    onclick={(e) =>
      alert(`${e.target.dataset.date} | ${e.target.dataset.value}`)}
  />
</div>
