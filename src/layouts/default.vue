<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <List :user="user"/>
    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Application</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref, onMounted } from 'vue'
  import List from '../components/List.vue'
  import axios from 'axios'

  const user = ref({})

  async function loadUser(){
  try{
    const response = await axios.get('https://reqres.in/api/users/2')
    console.log(response.data.data);
    user.value = response.data.data
  }
  catch(e){
    console.log(e);
  }
}

  onMounted(() => {
    console.log('apareci');
    loadUser()
  })

  const drawer = ref(null)
</script>
