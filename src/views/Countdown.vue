<template>
  <div>
    <h3>Countdown until: {{ date }}</h3>
    <counter-boxes :date="date"/>
    <create-another/>
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
