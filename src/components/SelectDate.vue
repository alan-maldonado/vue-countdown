<template>
  <section class="bg-light">
    <div class="container">
      <datetime
        v-model="date"
        type="datetime"
        input-class="datetime-input"
        placeholder="pick a date"
      ></datetime>
      <router-link class="btn btn-primary" :to="countdownLink">Get your link</router-link>
    </div>
  </section>
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
      date: ''
    }
  },
  computed: {
    countdownLink () {
      if (!this.date) {
        return ''
      }

      return `/${encodeURIComponent(this.date)}`
    }
  }
}
</script>
