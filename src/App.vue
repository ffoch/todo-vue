<script setup>
import {reactive} from 'vue'
import Displaycomp from './components/Displaycomp.vue'
import Formcomp from './components/Formcomp.vue'
import Buttoncomp from './components/Buttoncomp.vue'
import Listcomp from './components/Listcomp.vue'

let estado = reactive({
  resposta: 0,
  numero1 : '',
  numero2 : '',
  operador: '',
  listas: []
})

function calcularOperacao(numa,numb,o){
  const a = Number(numa)
  const b = Number(numb)
  switch(o){
    case "+":  estado.resposta = a+b;  break;
    case "-":  estado.resposta = a-b;  break;
    case "*":  estado.resposta = a*b;  break;
    case "/":  estado.resposta = a/b;  break;
  }
}

const atualizarVariaveis = (v,b) => {
  switch(b){
    case "1":
      estado.numero1 = v;
      calcularOperacao(estado.numero1, estado.numero2, estado.operador);
      break;
    case "2":
      estado.numero2 = v;
      calcularOperacao(estado.numero1, estado.numero2, estado.operador);
      break;  
  }
}

const mudarOperador = (o) => {
  estado.operador = o;
  calcularOperacao(estado.numero1, estado.numero2, estado.operador);
}

const limparTela = () =>{
  estado.operador = '';
  estado.numero1 = '';
  estado.numero2 = '';
  estado.listas =[];
}

const addLista = () => {
  if (estado.operador==''){
    estado.listas.push("error: missing math operator")
  }else{
    if (estado.numero1=='' || estado.numero2==''){
      estado.listas.push("error: missing number")
    }else{
      estado.listas.push(`${estado.numero1} ${estado.operador} ${estado.numero2} = ${estado.resposta}`);
    } 
  }
  
}

</script>

<template>

<div class="row d-flex">
  <div class="calculator pt-5 d-flex flex-column align-items-center col-md-8">
    <Displaycomp 
      :num1 = "estado.numero1"
      :num2 = "estado.numero2"
      :ope = "estado.operador"
      :res = "estado.resposta" />

    <Formcomp
      :num1="estado.numero1"
      :num2="estado.numero2"
      :ope="estado.operador"
      :atualizarVariaveis="atualizarVariaveis"
      :mudarOperador="mudarOperador"
      @update:num1="estado.numero1 = $event"
      @update:num2="estado.numero2 = $event"
      @update:ope="estado.operador = $event"
    />
    <Buttoncomp
      :limpa = "limparTela"
      :adiciona = "addLista"
      
    />
      <!-- <form @submit.prevent class="operators p-5 mb-4 mt-4 d-flex justify-content-center">
        <button type="button" class="fs-1 ms-3 me-3 p-3 rounded-5" @click="limparTela()">C</button>
        <button type="button" class="fs-1 ms-3 me-3 p-3 rounded-5" @click="addLista()">></button>
      </form> -->
  </div>
  
  <div class="list pt-5 ps-4 col-md-4">

    <Listcomp
      :lis = estado.listas
    />
    <!-- <div class="list-items">
      <p>log:</p>
      <ul>
        <li v-for="lista in estado.listas">{{ lista }}</li>
      </ul>
    </div> -->
  </div>
</div>

</template>

<style scoped>

*{
  border: 0;
  padding: 0;
  box-sizing: border-box;
}
img{
  height: 30px;
}
a{
  cursor: pointer;
  text-decoration: none;
}
.operator{
  color: silver;
}

.row{
  display: flex;
  background-color: #22252D;
  color: silver;
  width:100%;
  height: 100vh;
}

footer{
  background-color: #16181c;

}
</style>
