
<template>
  
  <main class=" app">

    <section class="greeting">
      <h2 class="title">
        Contact List
      </h2>
    </section>


    <section class="create-contactlist">
      <h3>Create Your Contact List</h3>
      <form @submit.prevent="addC">
        <input type="text" placeholder="Enter Contact Name" v-model="newConName">
        <input type="text" placeholder="Enter Contact Number" v-model="newConNum">
        <button id="addbutt" type="submit">Add Contact</button>
      </form>
    </section>


    <section class="contactlist">
      <div class="savedCon">
        <h2 class="listTitle">Saved Contacts</h2>
        <ul>
          <li v-for ="(contact, index) in contacts" :key="index">
            {{ contact.name }} ...... {{ contact.num }}
            <button class = "close" @click = "removeContact(index)">DELETE</button>
          </li>
        </ul>
      </div>
    </section>

  </main>

</template>

<script setup>
import {ref, onMounted, watch} from 'vue'


const newConName=ref('');
const newConNum=ref('');

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

function removeContact(index){
  contacts.value.splice(index, 1);
}

onMounted( () =>{
  contacts.value = JSON.parse(localStorage.getItem('contacts')) || []
})

watch(contacts, (newVal) => {
  localStorage.setItem('contacts',JSON.stringify(newVal))
},{deep: true})


</script>

