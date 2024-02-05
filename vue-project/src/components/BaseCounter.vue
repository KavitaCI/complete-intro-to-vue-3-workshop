<script>
export default {
  props: {
    counter: {
      type: Number,
      required: true
    }
  },
  emits: ['increment'],
  data() {
    return {
      msg: 'Hello world',
      comments: 'You have successfully created this Vue app'
    }
  }
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3 class="green">{{ comments }}</h3>
    <div>Count: {{ this.counter }}</div>
    <Button @click="$emit('increment')">Increment Count</Button>
  </div>
</template>
