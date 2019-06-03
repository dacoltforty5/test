<template>
  <section class="container">
    Name: <input v-model="sugarcoin.name" /> Price:
    <input v-model="sugarcoin.price" />
    <button @click="createSugarCoin">Create Sugar Coin</button>
  </section>
</template>

<script>
/* eslint-disable no-console */
// import Logo from '~/components/Logo.vue'

export default {
  components: {},
  data() {
    return {
      sugarcoin: {
        name: '',
        price: ''
      }
    }
  },
  async created() {
    const sugarcoins = await this.$axios.get('sugarcoins')
    console.log('SUGAR COINS', sugarcoins)
  },
  methods: {
    testFunc() {
      // eslint-disable-next-line no-console
      console.log('TEST')
    },
    async createSugarCoin() {
      console.log('Name', this.sugarcoin.name)
      console.log('price', this.sugarcoin)
      // console.log('Value', this.value)

      await this.$axios.post('sugarcoins', {
        name: this.sugarcoin.name,
        price: this.sugarcoin.price
      })
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
