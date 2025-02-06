
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
      <div class="savedCon">
        <h2 class="listTitle">Saved Contacts</h2>
        <ul>
          <li v-for ="(contact, index) in contacts" :key="index">
            {{ contact.name }} ...... {{ contact.num }}
            <button class = "close" @click = "removeContact(index)">X</button>
          </li>
        </ul>
      </div>
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

function removeContact(index){
  contacts.value.splice(index, 1);
}

</script>

