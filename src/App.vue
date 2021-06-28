<template>
  <textarea 
    type="text" 
    class="sentence"
    v-model="words"
  />
  <button @click="splitWords">split</button>
  <p>{{ words }}</p>
  <p>{{ splittedWords }}</p>
  <button v-if="splittedWords.length" @click="displayWords">start</button>
  <p>{{ currentWord }}</p>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      words: '',
      splittedWords: [],
      currentWord: ''
    }
  },
  methods: {
    splitWords() {
      this.splittedWords = this.words.trim().split(' ')
    },
    
    displayWords() {
      this.currentWord = this.splittedWords[0]
      this.splittedWords.splice(0, 1)
    }
  }
};
</script>

<style>

</style>
