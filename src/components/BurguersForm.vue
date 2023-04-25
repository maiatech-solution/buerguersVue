<template>
  <div class="container-geral">
   <Messege :msg="msg" v-show="msg"/>
    <div id="form-geral">
      <form id="burguer-form" @submit="createBurguer">
        <div class="input-container">
          <label for="nome">Nome do cliente:</label>
          <input
            type="text"
            id="nome"
            v-model="nome"
            placeholder="Digite seu nome"
          />
        </div>
        <div class="input-container">
          <label for="pao">Escolha o pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{pao.tipo}}</option>
          </select>
        </div>
        <div class="input-container">
          <label for="carne">Escolha a carne do seu Burguer:</label>
          <select name="carne" id="carne" v-model="carne">
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>
          </select>
        </div>
        <div class="input-container" id="opcionais-container">
          <label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
          <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
            <input
              type="checkbox"
              name="opcionais"
              :value="opcional.tipo"
              v-model="opcionais"
            />
            <span>{{opcional.tipo}}</span>
          </div>
        </div>
        <div class="input-container">
           <input type="submit" class="submit-btn" value="Criar meu burguer">
          </div>
      </form>
    </div>
  </div>
</template>

<script>
import Messege from './Messege.vue'

export default {

  name: "BurguersForm",
  data(){
    return {
      Selecionesuacarne: 'Selecione sua carne',
      paes: null,
      carnes: null,
      opcionaisdata: null,
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      msg: null
    }
  },
  components:{
    Messege
  },
  methods: {
    // Pegando dados do backend (get)
      async getIngredientes(){
        const req = await fetch('http://localhost:3000/ingredientes');
        const data = await req.json();

       
        this.paes = data.paes;
        this.carnes = data.carnes;
        this.opcionaisdata = data.opcionais;

      },

      // Adicionando dados no backend (post)
      async createBurguer(e){
        e.preventDefault();

        const data = {
          nome: this.nome,
          carne: this.carne,
          pao: this.pao,
          opicionais: Array.from(this.opcionais),
          status: "Solicitado"
        }
        
        const dataJson = JSON.stringify(data);

        const req = await fetch('http://localhost:3000/burgers',{
          method: 'POST',
          headers:{'Content-Type':'application/json'},
          body: dataJson
        });

        const res = await req.json();

        //chamando msg do sistema
        this.msg = `Pedido nº ${res.id} realizado com sucesso!`

        //limpar msg do sistema
        setTimeout(()=> this.msg = '', 5000)
       

       // limpar campos
       this.nome = '';
       this.carne = '';
       this.pao = '';
       this.opcionais = '';
      }
    },
    mounted(){
      this.getIngredientes()
    }
};
</script>

<style scoped>
    .container-geral{
        margin: 50px;
        display: flex;
        flex-direction: column;
    }
    #form-geral{
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    #burguer-form{
       max-width: 400px; 
       margin: 0 auto;
       align-items: center;
       display: flex;
       flex-direction: column;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 10px;
        justify-content: center;
        width: 100%;
    }
    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: #dddddd;
        padding: 5px 10px;
        border-left: 4px solid #fcba03;
    }

    input, select {
        padding: 10px;
        width: 300px;
    }

    #opcionais-title{
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
    }
    .checkbox-container span,
    .checkbox-container input{
        width: auto;
    }

    .checkbox-container span{
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn{
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
        margin-top: 10px;
    }
    .submit-btn:hover{
        background-color: transparent;
        color: #222;
    }
</style>