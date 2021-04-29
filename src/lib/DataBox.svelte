<script>
  export let stats

  let formatNumber = n => n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
</script>

<section class="grid md:grid-cols-2 gap-4">
  <div class="shadow-md bg-blue-100 p-10 text-center rounded">
    <h3 class="text-3xl text-blue-900 font-bold mb-4"> Cases </h3>
    <p class="text-2xl-mb-4"> <span class="font-bold"> New: </span> {formatNumber(stats.NewConfirmed)} </p>
    <p class="text-2xl-mb-4"> <span class="font-bold"> Total: </span> {formatNumber(stats.TotalConfirmed)} </p>
  </div>

  <div class="shadow-md bg-blue-200 p-10 text-center rounded">
    <h3 class="text-3xl text-blue-900 font-bold mb-4"> Deaths </h3>
    <p class="text-2xl-mb-4"> <span class="font-bold"> New: </span> {formatNumber(stats.NewDeaths)} </p>
    <p class="text-2xl-mb-4"> <span class="font-bold"> Total: </span> {formatNumber(stats.TotalDeaths)} </p>
  </div>
</section>