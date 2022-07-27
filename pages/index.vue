<template>
  <main>
    <button @click="onButtonClick">Click me</button>
  </main>
</template>

<script>
export default {
  name: 'IndexPage',
  async created() {
    console.log(await this.$axios.$get('/api/v3/ticker/24hr'))
  },
  data(){
    return{
      error:'',
    }
  },
  methods:{
    async onButtonClick() {
      this.error=''
      try {
        const data = await this.$axios.$get('/api/v3/ticker/24hr');
        console.log(data);
      } catch (e) {
        this.error="There was an error"
        console.log(e)
      }
    }
  }
}
</script>
