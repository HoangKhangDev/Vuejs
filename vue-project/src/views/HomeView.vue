<script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <main class="counter-home">
    <!-- <TheWelcome /> -->
    <h1>{{  CountData.titleCounter  }}</h1>
    <div>
      <button @click="decrement(2)" class="btn">--</button>
      <button @click="decrement(1)" class="btn">-</button>
      <span class="counter">{{CountData.counter}}</span>
      <button @click="increment(1)" class="btn">+</button>
      <button @click="increment(2)" class="btn">++</button>
    </div>
    <p>This counter is {{  chanOrLe }}</p>
    <div class="edit">
      <span>Edit couter title :</span>
      <input type="text" v-model="CountData.titleCounter" />
    </div>
  </main>
</template>

<script >

import { reactive ,computed, watch } from 'vue';
const CountData = reactive({
  counter: 10,
  titleCounter: "TitleCounter"
})

const decrement = count =>{
  CountData.counter-=count;
}
const increment = count=>{
  CountData.counter+=count;
}

const chanOrLe = computed(()=>{
  if(CountData.counter%2===0) return "Chan";
  return "Le"
});

watch(()=>CountData.counter,(counternow,counterold)=>{
  console.log("Counter Now: "+counternow);
  console.log("Counter Old: "+counterold);
  if(counternow>20)
  alert("Complete")
});

// ref
// import { ref } from 'vue' ;
// const counter =ref(10);
// const titleCounter = ref("TitleCounter");

// const increment = () => {
//       counter.value++;
// }
    
// const decrement = () => {
//       counter.value--;
// }

</script>

<style>
.counter{
  font-size: 39px;
}
.btn{
  font-size: 39px;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
  border: 1px solid black;
  background-color: white;
  color: black;
  cursor: pointer;
}
.edit{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.edit span{
  font-size: 30px;
}
</style>