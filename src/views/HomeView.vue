<template>
  <Banner/>
  <div class="main-container">
   <h1>Monte seu Pedido:</h1>
   <Form/>
  </div>
</template>

<script>
import Banner from '../components/Banner.vue'
import Form from '../components/Forms.vue'

export default {
  name: 'Home',
  components: {
    Banner,
    Form
  },  
  
}
</script>


<style >
  
</style>