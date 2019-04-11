<template>
  <div>
    <div id="status-legend" v-if="completed">
      <h4>Yay!! You have reached your countdown</h4>
    </div>
    <div class="boxes-list" v-else>
      <counter-box v-model="days" legend="days"/>
      <counter-box v-model="hours" legend="hours"/>
      <counter-box v-model="minutes" legend="minutes"/>
      <counter-box v-model="seconds" legend="seconds"/>
    </div>
  </div>
</template>

<script>
import CounterBox from './CounterBox'
import { clearInterval } from 'timers'
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
    const timer = setInterval(this.computeDate, 1000)
    if (this.completed) {
      clearInterval(timer)
    }
  }
}
</script>
