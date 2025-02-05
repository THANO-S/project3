
<template>
  
  <main class=" app">

    <section class="greeting">
      <h2 class="title">
        <input type="text" placeholder="Enter Your Name" v-model="name">'s Contact List
      </h2>
    </section>


    <section class="create-contactlist">

    </section>


    <section class="contactlist">

    </section>




  </main>


</template>

<script setup>
import {ref} from 'vue'

const username=ref('')


</script>

