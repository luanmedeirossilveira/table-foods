<template>
<div id="box">
  <input 
    id="input"
    @keyup.enter="addFood"
    type="text" 
    v-model="currentFood"
    placeholder="Coloque Aqui!" />
  <input 
    type="text" 
    v-model="currentPrices"
    placeholder="Coloque Valor!" />
  <button 
    @click="addFood">
    Adicionar
  </button>
  <button
    id="btn_reset"
    @click="reseta">
    Resetar
  </button>
  <button 
    class="exclui" 
    @click="exclui">
    Excluir
  </button>
  <br>
  <food-list 
    @stop="handleStop"
    :foods="foods"/>
</div>
</template>

<script>
import FoodList from './components/foodList'

export default {
  components: { FoodList },
  data: () => ({
    currentFood: "",
    currentPrices: "",
    link: "http://www.g1.globo.com",
    foods: ['Maçã', 'Pera'],
    prices: [5, 2]
  }),
  methods: {
    handleStop (payload) {
      console.log("Payload => ", payload)
      alert(payload)
      document.getElementById("input").disabled = true
    },
    addFood () {
      if(this.currentFood != ""){
        this.foods.push(this.currentFood)
        alert(this.currentPrices)
        this.prices.push(this.currentPrices)
      }else
        alert("Campo vazio!")
      this.currentFood = ''
      this.currentPrices = ''
    },
    reseta () {
      window.location.reload()
    },
    exclui () {
      this.foods.pop()
    }
  }
}
</script>
<style>
body{
  text-align: center;
  background-color:#fff;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
*{
  box-sizing: border-box;
}
#box{
  padding: 50px;
}
input{
  width: 200px;
  height: 50px;

  margin: 2px;
  text-align: center;

  border: none;
  border-bottom: 2px solid #FF9F1C;

  background-color: none;
  color: #FF9F1C;
  font-weight: 800;
}
input::placeholder{
  color: #FF9F1C;
}
input:focus{
  outline: none; /* Retira a borda quando focar */
  transition-duration: 2s;
}
button{
  width: 200px;
  height: 56px;

  margin: 2px;
  border: 1px solid #FF9F1C;
  border-radius: 10px;

  cursor: pointer;

  color: #FF9F1C;
  background: transparent;
  text-transform: uppercase;
  font-weight: 800;
}
button:focus{
  outline: none;
}
#btn_reset{
  color: rgb(255, 0, 0);
  border: 1px solid #ff0000;
}
.box_list{
  margin: 20px 20px 20px -15px;
}
ul{
  margin: 0 auto;
  width: 50%;
  text-align: left;
}
ul li:hover{
  background: #ecbc98;
  cursor: pointer;
}
ul li:nth-child(n){
  list-style: none;
  padding: 20px;
  color: #EE8434;
}
ul li:last-child{
  list-style: none;
  padding: 20px;
  border-bottom: none;
  color: #EE8434;
}
.exclui{
    border: 1px solid #3066BE;
    background-color: transparent;
    color: #3066BE;
}
</style>