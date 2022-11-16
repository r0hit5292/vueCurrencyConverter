<template>
    <div class=" bg-black" >
     
     <input v-model="INPUT"  type="number" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username"  placeholder="enter currency">
 
     <select class="block w-full px-2 py-1 text-sm font-normal text-gray-700"  id="firstCurrency" v-model="FirstValue">
                 <option v-for="(curr, index) in Country" :value="index" :key="index">{{Country[index]}}</option>
             </select>
             <select class="block w-full px-2 py-1 text-sm font-normal text-gray-700" id="SecondCurrency" v-model="SecondValue">
              <template v-for="(curr, index)  in Country" :key="index" >
                     <option v-if="index!=Number(FirstValue)" :value="index" >{{Country[index]}}</option>
                 </template>
             </select>
    
     <button @click="Converter" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mx-9 my-9">
         Convert
 </button>
    <p >{{ans}}</p>
 </div>
 </template>
 <script setup lang="ts">
 import { ref ,watch} from 'vue';
 var msg = ref();
 var INPUT=ref();
 const FirstValue = ref();
 const SecondValue = ref();
 var ans: any= ref();
 const Country = ["KWD","BHD","OMR","BP","EUR","USD","BND","NZD","AWG","INR"];
 const Currency = [0.31,0.38,0.39,0.88,1.01,1.00,1.43,1.74,1.80,81.40];
 function Converter(){
     ans.value  = ref((Currency[SecondValue.value]/Currency[FirstValue.value])*INPUT.value);
     console.log(ans.value)
  ans.value= ans.value.value.toFixed(2)
  
 }
 </script>

