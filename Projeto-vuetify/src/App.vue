<template>
  <v-app >

    <v-app-bar flat color="purple" class="border-b">

      <v-app-bar-title>LUNIO</v-app-bar-title>

    </v-app-bar>

    <v-navigation-drawer permanent color="purple" width="flex" expand-on-hover rail >

      <v-list-item
       title="Dashboard"
      prepend-avatar=".\assets\logo.png"

       >
      </v-list-item>
      <v-divider></v-divider>
      <v-list-group link title="Produtos"></v-list-group>
      <v-divider></v-divider>
      <v-list-item link title="Negocios"></v-list-item>
      <v-divider></v-divider>
      <v-list-item link title="Cadastro"></v-list-item>
      <v-divider></v-divider>

    </v-navigation-drawer>
    <v-main>
      
        <v-container>
          <h1>Dashboard</h1>
          <v-row>
            <v-col cols="4" > oi</v-col>
            <v-col cols="4" > ola</v-col>
            <v-col cols="4" >eae</v-col>
          </v-row>
        </v-container>

        <HelloWorld></HelloWorld>
    
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
//
</script>
