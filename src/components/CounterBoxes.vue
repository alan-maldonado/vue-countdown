<template>
  <div>
    <div v-if="completed">
      <h4>Yay!! You have reached your countdown</h4>
    </div>
    <div v-else>
      <CounterBox v-model="days" legend="days"/>
      <CounterBox v-model="hours" legend="hours"/>
      <CounterBox v-model="minutes" legend="minutes"/>
      <CounterBox v-model="seconds" legend="seconds"/>
    </div>
  </div>
</template>

<script>
import CounterBox from './CounterBox'
export default {
  name: 'counter-boxes',
  components: {
    CounterBox
  },
  props: {
    date: {
      type: Object, // momentjs instance
      default: null
    }
  },
  data () {
    return {
      days: null,
      minutes: null,
      hours: null,
      seconds: null,
      completed: false
    }
  },
  methods: {
    computeDate () {
      const now = new Date().getTime()
      const diff = this.date.diff(now)

      this.days = Math.floor(diff / (1000 * 60 * 60 * 24))
      this.hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
      this.minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))
      this.seconds = Math.floor((diff % (1000 * 60)) / 1000)

      if (this.seconds < 0) {
        this.completed = true
      }
    }
  },
  created () {
    this.computeDate()
    setInterval(this.computeDate, 1000)
  }
}
</script>
