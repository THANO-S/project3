
<template>
  
  <main class=" app">

    <section class="greeting">
      <h2 class="title">
        <input type="text" placeholder="Enter Your Name" v-model="name">'s Contact List
      </h2>
    </section>


    <section class="create-contactlist">
      <h3>Create Your Contact List</h3>
      <form @submit.prevent="addC">
        <input type="text" placeholder="Enter Contact Name" v-model="newConName">
        <input type="text" placeholder="Enter Contact Number" v-model="newConNum">
        <input type="submit" value="Add Contact"/>
      </form>
    </section>


    <section class="contactlist">

    </section>




  </main>


</template>

<script setup>
import {ref} from 'vue'

const name =ref('');
const newConName=ref('');
const newConNum=ref('');
//array to store contacts
const contacts=ref([]);

const addC = () => {
  if(newConName.value.trim() === '' || newConNum.value.trim() ===''){
    alert('Please provide a name and phone number.')
    return
  }

  contacts.value.push({
    name: newConName.value,
    num: newConNum.value,
  })

  newConName.value = ''
  newConNum.value = ''
}

</script>

