<template>
  <div>
    <h1>Faktid numbrite kohta</h1>
    <p>Huvitavad faktid numbrite kohta</p>
    <input type="number" min="0" v-model="number">
    <input type="number" min="0" v-model="increment">
    <p v-for="value in data">{{ value }}</p>
  </div>
</template>

<script>
const axios = require('axios')

export default {
  name: 'Faktid',
  data () {
    return {
      data: '',
      number: 0,
      increment: 0
    }
  },
  watch: {
    number() {
      this.getFact()
    },
    increment() {
      this.getFact()
    }
  },
  methods: { 
    getFact () {
     
      if (this.number !== '' && this.increment !== '') {
        let url = `http://numbersapi.com/${this.number}..${parseInt(this.number) + parseInt(this.increment)}`

      axios.get(url)
          .then(response => {
            //console.log(response.data)
            this.data = response.data
          })
          .catch(error => {
            console.log(error)
        })
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
