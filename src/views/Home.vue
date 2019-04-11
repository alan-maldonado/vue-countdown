<template>
  <div>
    <header class="bg-dark">
      <h3 class="container">Countdown</h3>
    </header>
    <select-date/>
  </div>
</template>

<script>
import SelectDate from '../components/SelectDate'

export default {
  name: 'home',
  components: {
    SelectDate
  }
}
</script>
