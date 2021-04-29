<script>
  import Header from './lib/Header.svelte'
  import DataTitle from './lib/DataTitle.svelte'
  import DataBox from './lib/DataBox.svelte'
  import CountrySelect from './lib/CountrySelect.svelte'

  import loadingImage from './assets/hourglass.gif'

  let loading = true
  let title = ''
  let stats = {}
  let dataDate = ''
  let countries = []
  
  function onCountryChange(event) {
    const country = event.detail
    title = country.Country
    stats = country
  }

  async function fetchAndSetData() {
    loading = true

    const res = await fetch('https://api.covid19api.com/summary')
    const data = await res.json()

    title = 'Global'
    stats = data.Global
    dataDate = data.Date
    countries = data.Countries

    loading = false
  }

  fetchAndSetData()

</script>

<Header />
<div class="container">
  {#if !loading}
    <DataTitle title={title} dataDate={dataDate} />
    <DataBox stats={stats} />
    <CountrySelect countries={countries} on:country-change={onCountryChange}/>
    {#if stats.Country}
      <button
        class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
        on:click={fetchAndSetData}
      > See Global Stats </button>
    {/if}
  {:else}
    <main class="flex flex-col align-center justify-center text-center">
      <p class="text-gray-500 text-3xl mt-10 mb-6"> Fetching Data... </p>
      <img src={loadingImage} class="w-24 m-auto" alt="">
    </main>
  {/if}
</div>