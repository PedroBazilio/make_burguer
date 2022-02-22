<template>
  <ul class="header">
        <li class="logo-url">
          <router-link to='/' >
              <img :src="logo" :alt="alt" id="logo">
          </router-link>
        </li>
        
        <li>
          <router-link to="/">INICIO</router-link>
        </li>

        <li>
          <router-link to="/pedidos">PEDIDOS</router-link>
        </li>
        
  </ul>
</template>

<script>
export default {
    name:'Header',
    props: ['logo', 'alt']

}
</script>

<style scoped>
  .header {
    background-color: rgb(241, 231, 236);
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    padding-right: 80px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    list-style-type: none;
  }
  .header .logo-url {
    margin: auto;
    margin-left: 0;
  }
  #logo {
    width: 60px;
    height: 60px;
  }
  .header a {
    color: #6e6448;
    text-decoration: none;
    margin: 12px;
    margin-right:5px ;
    transition: .5s;
  }
  .header a:hover {
    color: rgb(219, 63, 63);
  }
</style>
