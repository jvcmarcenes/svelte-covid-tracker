<script>
  import { createEventDispatcher } from "svelte";

  export let countries

  const dispatch = createEventDispatcher()
  let value

  function onChange() {
    const country = countries.find(i => i.ID === value)

    dispatch('country-change', country)
  }
</script>

<!-- svelte-ignore a11y-no-onchange -->
<select class="form-select mt-10 w-full border p-3 rounded" bind:value on:change={onChange}>
  <option value="0"> Select Country </option>
  {#each countries as country}
    <option value={country.ID}> {country.Country} </option>
  {/each}
</select>