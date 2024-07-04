<template>
<v-container >
    <v-form >
      <!-- INPUT NOME -->
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="newClient.nome"
            label="Nome"
            placeholder="Fulano Beltrano"
            variant="outlined"
            clearable
          ></v-text-field>
        </v-col>
      </v-row>

      <!-- INPUT ENDEREÇO -->
      <v-row>
        <v-col cols="10">
          <v-text-field
             v-model="newClient.endereço"
            label="Endereço"
            placeholder="Rua dos Bobos"
            variant="outlined"
            clearable
          ></v-text-field>
        </v-col>
        <!-- INPUT NUMERO DO ENDEREÇO -->
        <v-col cols="2">
          <v-text-field
            v-model="newClient.numero"
            label="Número"
            placeholder="0"
            variant="outlined"
            clearable
          ></v-text-field>
        </v-col>
      </v-row>

      <!-- INPUT TELEFONE -->
      <v-row>
        <v-col cols="12">
          <v-text-field
            v-model="newClient.telefone"
            label="Telefone"
            placeholder="(81)95555-5555"
            variant="outlined"
            clearable
          ></v-text-field>
        </v-col>
      </v-row>
      
      <!-- INPUT EMAIL -->
      <v-row>
        <v-col cols="12">
          <v-text-field
          v-model="newClient.email"
            label="Email"
            placeholder="xxxxx@gmail.com"
            variant="outlined"
            clearable
          ></v-text-field>
        </v-col>
      </v-row>

      <!-- BUTTON -->
      <v-row>
        <v-col cols="12" class="text-center">
          <v-btn variant="outlined" class="btn">Salvar</v-btn>
        </v-col>
      </v-row>
    </v-form>
    
    <v-divider></v-divider>
    
      
    </v-container>

  <v-container>
    <!-- v-data-table é o componente de tabela do Vuetify -->
    <!-- Define os cabeçalhos da tabela -->
    <!-- Define os dados que serão exibidos na tabela -->
    <!-- Adiciona uma sombra de elevação para o estilo -->
    <v-data-table :headers="headers" :items="clients" item-key="id">
      <!--  Slot para o topo da tabela -->
      <template v-slot:top>
        <v-toolbar flat>
          <v-toolbar-title>Clientes</v-toolbar-title>
          <!-- Título da toolbar -->
        </v-toolbar>
      </template>
      
      <!-- Slot para as ações na tabela -->
      <template v-slot:item.actions="{ item }">
        <v-icon class="me-2" size="small" @click="editClient(item)">
          mdi-pencil
        </v-icon>
        <v-icon size="small" @click="deleteClient(item)"> mdi-delete </v-icon>
      </template>

      <template v-slot:no-data>
        <v-btn color="primary">Reset</v-btn>
      </template>
    </v-data-table>
  </v-container>
</template>

<script>

import axios from 'axios';

export default {
  data() {
    return {
      headers: [
        { title: "ID", align: "start",  value: "id" },
        { title: "Nome", align: "start",  value: "nome" },
        { title: "Endereço", align: "end", value: "endereço" },
        { title: "Número", align: "end", value: "numero" },
        { title: "Telefone", align: "end", value: "telefone" },
        { title: "Email", align: "end", value: "email" },
        { title: "Ações", align: "end", value: "actions", sortable: false }
      ],
      clients: [],
      newClient: {
        nome: '',
        endereço: '',
        numero: '',
        telefone: '',
        email: ''
      }
    };
  },
  created() {
    this.loadClients();
  },
  methods: {
    async loadClients() {
      try {
        const response = await axios.get("../../api/clientes.json");
        if (response.data && response.data.clientes) {
          this.clients = response.data.clientes;
        } else {
          console.error('Dados recebidos não contêm um array "clientes":', response.data);
        }
      } catch (error) {
        console.error("Erro ao carregar dados dos clientes:", error);
      }
    },
    async addClient() {
      try {
        // Here, you would normally make a POST request to your server to add the client
        // For this example, we'll just log the new client data and add it to the list
        const newClientId = this.clients.length ? this.clients[this.clients.length - 1].id + 1 : 0;
        const newClient = { id: newClientId, ...this.newClient };
        this.clients.push(newClient);
        
        // Clear the form fields
        this.newClient = {
          nome: '',
          endereço: '',
          numero: '',
          telefone: '',
          email: ''
        };

        console.log("Novo cliente adicionado:", newClient);

        // Save the updated clients list to the server (example with a PUT request)
        await axios.put('/api/clientes.json', { clientes: this.clients });

      } catch (error) {
        console.error("Erro ao adicionar cliente:", error);
      }
    },




  },
};
</script>

<style>
  .btn {
  background-color: green !important;
  color: white !important;
  margin: 10px;
}
</style>