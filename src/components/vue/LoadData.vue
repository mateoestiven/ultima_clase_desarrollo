<script setup>

import { ref } from "vue";

const users = ref([])

function loadData() {
    fetch('https://jsonplaceholder.typicode.com/users')
  .then(function(response){
    return response.json()
  })
  .then(function(data){
    console.log(data);
    users.value = data
  });
}
</script>

<template>
    <div 
    v-for="user in users"
    :key="user.id"
    class="bg-purple-500 mb-1 text-center w-1/5 mx-auto rounded-xl p-2 ">
    {{ user.name }}
    </div>
    <div class="w-full flex justify-center items-center">
    <button class="bg-purple-400 p-2 rounded-xl font-semibold border border-black " @click="loadData">
        Cargar info
    </button>
</div>
</template>