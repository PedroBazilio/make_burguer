<template>
  <Header :logo='logoSrc' :alt='appName'/>
  <router-view/>
  <Footer />
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
export default {
  components: {Header, Footer},
  data(){
    return{
      logoSrc: '/img/OpenmojiFlagTurkey.svg',
      appName: 'Free Ukraine'
    }
  }
}
</script>

<style>
  *{
    font-family: Arial, Helvetica, sans-serif;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  .main-container{

    margin: 50px;
    min-height: 250px;
  }

  h1{
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: rgb(77, 73, 73);
  } 
</style>
