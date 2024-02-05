<script>
import HelloWorld from './components/HelloWorld.vue'
import BaseCounter from './components/BaseCounter.vue'
import SlotButton from './components/SlotButton.vue'
import Structure from './components/Structure.vue'

export default {
  components: {
    HelloWorld,
    BaseCounter,
    SlotButton,
    Structure
  },

  data() {
    return {
      title: 'The Simpsons',
      seasons: 12,
      Characters: { Simpsons: ['Bart', 'Lisa', 'Marge', 'Homer', 'Maggie'], Flanders: ['Ned'] },
      newCharacter: '',
      counter: 1
    }
  },
  computed: {
    bigNumber() {
      return this.newCharacter.length * 10
    }
  },
  methods: {
    isInputValid() {
      const regex = /^[a-zA-Z\s]+$/
      return regex.test(this.newCharacter.trim())
    },
    addCharacter() {
      if (this.isInputValid() && this.newCharacter.trim() !== '') {
        this.Characters = {
          ...this.Characters,
          Flanders: [...this.Characters.Flanders, this.newCharacter.trim()]
        }
        this.newCharacter = '' // Clear input after adding character
      }
    },
    incrementCounter() {
      this.counter += 1
    }
  }
}
</script>

<template>
  <Structure>
    <template #beginning>
      <HelloWorld />
    </template>
    <template #medium>
      <SlotButton>This is a slot button</SlotButton>
    </template>
    <template #end>
      <BaseCounter :counter="counter" @increment="incrementCounter" />
    </template>
    <!-- <template #firstName> Kavita </template> -->
    <template #firstName>Kavita</template>
  </Structure>
  <h1>Series Data</h1>
  <div id="app">
    <h2>{{ title }}</h2>
    <h4 v-if="seasons">Seasons: {{ seasons }}</h4>
    <h4 v-else>Upcoming series</h4>
    <h4>Characters:</h4>
    <ul v-for="(characters, familyName) in Characters" :key="familyName">
      <li>{{ familyName }}</li>
      <ul>
        <li v-for="character in characters" :key="character">{{ character }}</li>
      </ul>
      <div>total: {{ characters.length }}</div>
      <div v-if="familyName === 'Flanders'">
        <label for="addCharacter">Add character</label>
        <input type="text" v-model="newCharacter" />
        <span v-if="!isInputValid() && newCharacter">Please enter valid characters</span>
        <div><button type="submit" v-on:click="addCharacter">Submit</button></div>
      </div>
    </ul>
    <div>{{ bigNumber }}</div>
  </div>
</template>
