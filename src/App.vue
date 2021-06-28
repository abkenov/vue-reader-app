<template>
  <textarea 
    type="text" 
    class="sentence"
    v-model="words"
  />
  <button @click="splitWords">split</button>
  <p>Сколько слов в минуту хочешь читать?</p>
  <select v-model="speed">
    <option>60</option>
    <option>100</option>
    <option>400</option>
  </select>
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
      currentWord: '',
      re: /\s+|\n+|\t+/,
      speed: 100,
    }
  },
  methods: {
    splitWords() {
      if(this.words.length){
        this.splittedWords = this.words.trim().split(this.re)
      }
    },
    
    displayWords() {
      this.speed = 1000 / (this.speed / 60)

      if(this.splittedWords.length) {
        setInterval(() => {
          this.currentWord = this.splittedWords[0]
          this.splittedWords.splice(0, 1)
        }, this.speed)
      }
    },
  }
};
</script>

<style>
textarea {
  height: 555px;
  width: 1016px;
}
</style>
