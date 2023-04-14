<template>
  <div class="container-geral">
    <p>Componente de mensagem</p>
    <div id="form-geral">
      <form id="burguer-form">
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
            <option value="">Selecione ...</option>
            <option value="integral">Integral</option>
          </select>
        </div>
        <div class="input-container">
          <label for="carne">Escolha a carne do seu Burguer:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="">Selecione ...</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div class="input-container" id="opcionais-container">
          <label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="opcionais"
              value="salame"
              v-model="opcionais"
            />
            <span>Salame</span>
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
export default {
  name: "BurguersForm",
};
</script>

<style scoped>
    .container-geral{
        margin: 50px;
    }
    #form-geral{
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    #burguer-form{
       max-width: 400px; 
       margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 10px;
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

    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
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