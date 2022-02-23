<template>
   <div class="message-container">
       <p>{{msg}}</p>
   </div>
</template>

<script>
export default {
    name: 'Message',
    props: {
        msg: String
    }
}
</script>

<style>
    .message-container{
        text-align: center;
        color: #004085;
        background-color: #cce5ff;
        border: 2px solid #b8daff;
        border-radius: 5px;
        padding: 10px;
        margin: 30px auto;
        max-width: 400px;
         
    }
</style> 