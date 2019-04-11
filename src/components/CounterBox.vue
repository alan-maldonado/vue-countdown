<template>
  <div>
    <p>{{value}}</p>
    <p>{{legend}}</p>
  </div>
</template>

<script>
export default {
  name: 'time-box',
  props: {
    value: {
      type: Number,
      required: true
    },
    legend: {
      type: String,
      default: ''
    }
  }
}
</script>
