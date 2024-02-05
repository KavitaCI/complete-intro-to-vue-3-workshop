<script>
export default {
  data() {
    return {
      msg: 'Hello world',
      comments: 'You have successfully created this vue app'
    }
  }
}
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3 class="green">{{ comments }}</h3>
  </div>
</template>
