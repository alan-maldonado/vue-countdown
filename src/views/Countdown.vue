<template>
  <div>
    <header class="bg-dark">
      <h3 class="container">Countdown until: {{ date }}</h3>
    </header>

    <div class="container">
      <counter-boxes :date="date"/>
      <create-another/>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
import CounterBoxes from '../components/CounterBoxes'
import CreateAnother from '../components/CreateAnother'
export default {
  name: 'countdown',
  components: {
    CounterBoxes,
    CreateAnother
  },
  data () {
    return {
      date: moment(this.$route.params.date)
    }
  },
  created () {
    if (!this.date.isValid()) {
      // invalid date
      this.$router.push('/')
    }
  }
}
</script>
