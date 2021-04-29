<script>
  import moment from 'moment'

  export let title
  export let dataDate

  $: timestamp = moment(dataDate).format('MMMM Do YYYY, h:mm:ss a')
</script>

<section class="text-center">
  <h2 class="text-3xl font-bold"> {title} </h2>
  <p class="text-2xl mt-4 mb-10"> {timestamp} </p>
</section>