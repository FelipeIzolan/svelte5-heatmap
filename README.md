# 🔥 Heatmap.svelte

![image](https://github.com/user-attachments/assets/67412475-ec75-4bcf-980b-9cdc0ffbdfff)

A Svelte 5 heatmap component inspired by GitHub’s contribution graph

## 🚀 Getting Started

```
npm install Heatmap.svelte
```

```svelte
<script>
  import Heatmap from "$lib/Heatmap.svelte";

  let data = $state<{ [key: string]: number }>({});
  let year = 2025;
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

<div style="font-size:12px">
  <Heatmap
    {data}
    onclick={(e) => alert(`${e.target.dataset.date} | ${e.target.dataset.value}`)}
  />
</div>
```

## ⚙️ Props

- ``data`` - Object containing the chart data. Each key must be in ISO date format. `{ '2025-01-02': 5 }` **(required)** 
- ``colors`` - Array of colors to use for the chart, ordered from lowest to highest. (default = GitHub's graph colors)
- ``year`` - The heatmap year. (default = current year)
- ``lday`` - Adds day labels. (default = true)
- ``lmonth`` - Adds month labels. (default = true)
- ``onclick`` - onclick event.
- ``onmouseout`` - onmouseout event.
- ``onmouseover`` - onmouseover event.

> [!NOTE]
> The heatmap size is determined by the parent element's font size, as it uses **em** units.

## 📜 License

- [svelte](https://github.com/sveltejs/svelte) - MIT
- [sveltekit](https://github.com/sveltejs/kit) - MIT
- [Heatmap.svelte](https://github.com/FelipeIzolan/Heatmap.svelte) - MIT
