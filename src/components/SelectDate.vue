<template>
  <div>
    <h3>Pick a date to create your countdown</h3>
    <datetime v-model="date" type="datetime"></datetime>
    <router-link :to="countdownLink">Get your link</router-link>
  </div>
</template>

<script>
import { Datetime } from 'vue-datetime'

export default {
  name: 'select-date',
  components: {
    Datetime
  },
  data () {
    return {
      date: null
    }
  },
  computed: {
    countdownLink () {
      if (!this.date) {
        return null
      }

      return `/${encodeURIComponent(this.date)}`
    }
  }
}
</script>
