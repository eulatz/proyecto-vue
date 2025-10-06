
//reactivo:  para acceder al valor de counter, añadir .value (devuelve objeto con propiedad.value)
<script setup>
import {ref, computed} from "vue"

const counter = ref(0);
  const increment =() =>{
    counter.value ++
  }
  const dissmiss = () =>{
    counter.value--
  }
  const retorno = () =>{
    counter.value = 0
  }
  const classCounter = computed(()=> {
    if (counter.value === 0){
      return 'determinado'
    }
    if (counter.value > 0){
      return 'positive'
    }
    if (counter.value < 0){
      return 'negative'
    }
  })


const arrayFav = ref([])

  const fav = () => {
    arrayFav.value.push(counter.value)
  }

  const boqbtnadd = computed(()=> {
    const numsearch = arrayFav.value.find((num) => num === counter.value)
    return numsearch || numsearch===0
  })
</script>


<template>
<div class="container text-center mt-3">
  <h2 :class="classCounter" >{{counter}}</h2>
  <div class="btn-group">
    <button @click="increment" class="btn btn-success">aumentar contador</button>
    <button @click ="dissmiss" class="btn btn-danger">reducir contador</button>
    <button @click="retorno" class="btn btn-secondary">volver a 0</button>
    <button @click="fav" :disabled="boqbtnadd" class="btn btn-primary">Guardar fav</button>  
  </div>

<ul class="list-group mt-4">
  <li class="list-group-item" v-for="(num,index) in arrayFav" :key="index">
    {{num}}
  </li>
</ul>

</div>
</template>

<style>
.positive{
  color:green;
}
.negative{
  color:red;
}
.determinado{
  color:yellow;
}
</style>