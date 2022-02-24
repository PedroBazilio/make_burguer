<template>
  <div>
      <div id="burger-table">
          <Message :msg='msg' v-show="msg"/>
          <div>
              <div id="burger-table-heading">
                  <div class="order-id">#</div>
                  <div>Cliente</div>
                  <div>Pão</div>
                  <div>Carne</div>
                  <div>Acompanhamentos</div>
                  <div>Ações:</div>
              </div>
          </div>
          <div class="burger-table-rows">
              <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                  <div class="order-number">{{ burger.id }}</div>
                  <div>{{ burger.nome }}</div>
                  <div>{{ burger.pao }}</div>
                  <div>{{ burger.carne }}</div>
                  <div>
                      <ul v-for="(opcional, index) in burger.opcionais" :key="index">
                          <li>{{ opcional }}</li>
                      </ul>
                  </div>
                  <div>
                      <select name="status" classe="status" @change="updateBurger($event, burger.id)">
                          <option v-for="s in status" :key="s.id" :value="s.tipo" :selected='burger.status == s.tipo'>{{s.tipo}}</option>
                      </select>
                      <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
                  </div>
              </div>
          </div>
      </div>

  </div>
</template>

<script>
import Message from './Message.vue'

export default {
    name:'Dashboard',
    data() {
      return {
        burgers: null,
        burgerId: null,
        status: [],
        msg: null
      }
    },
    components:{
      Message
    },
    methods: {
      async getPedidos() {
        const req = await fetch('http://localhost:3000/burgers')
        const data = await req.json()
        this.burgers = data
        
        this.getStatus()
      },
      async getStatus(){
        const req = await fetch('http://localhost:3000/status')
        const data = await req.json()
        this.status = data
      },
      async deleteBurger(id){
        const req = await fetch(`http://localhost:3000/burgers/${id}`,{
          method: 'DELETE'
        });

        const res = await req.json()
        
         this.msg = `Pedido removido com sucesso!`;
      //limpar msg
      setTimeout(() => {
        this.msg = "";
      }, 5000);

        this.getPedidos();

      },
      async updateBurger(event, id){
        
        const option = event.target.value;
        const dataJSON = JSON.stringify({status:option});

         const req = await fetch(`http://localhost:3000/burgers/${id}`,{
           method: 'PATCH',
           headers: {'Content-Type':'application/json'},
           body: dataJSON
         });

         const res = await req.json();
          this.msg = `Pedido Nº${res.id} foi atualizado para ${res.status}!`;
          //limpar msg
          setTimeout(() => {
            this.msg = "";
          }, 5000);

      }
    },
    mounted() {
      this.getPedidos();
    },
}
</script>

<style scoped>
    #burger-table {
    max-width: 1200px;
    margin: 0 auto;
  }
  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }
  #burger-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
  }
  .burger-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
  }
  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }
  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }
  select {
    padding: 12px 6px;
    margin-right: 12px;
  }
  .delete-btn {
    background-color: rgb(73, 58, 58);
    color: rgb(241, 231, 236);
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: 0.5s;
  }
  
  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>