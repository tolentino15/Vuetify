<template>
  <v-container>
    <!-- INPUT NOME -->

    <v-row>
      <v-input>
        <v-text-field
          label="Nome"
          placeholder="Fulano Beltrano"
          variant="outlined"
          clearable
        >
        </v-text-field>
      </v-input>
    </v-row>

    <!-- INPUT ENDEREÇO -->
    <v-row>
      <v-col cols="10">
        <v-input>
          <v-text-field
            label="Endereço"
            placeholder="Rua dos Bobos"
            variant="outlined"
            clearable
          >
          </v-text-field>
        </v-input>
      </v-col>
      <!-- INPUT NUMERO DO ENDEREÇO -->
      <v-col cols="2">
        <v-input>
          <v-text-field
            label="Número"
            placeholder="0"
            variant="outlined"
            clearable
          >
          </v-text-field>
        </v-input>
      </v-col>
    </v-row>

    <!-- INPUT TELEFONE -->
    <v-row>
      <v-input>
        <v-text-field
          label="Telefone"
          placeholder="(81)95555-5555"
          variant="outlined"
          clearable
        >
        </v-text-field>
      </v-input>
    </v-row>
    <!-- INPUT EMAIL -->
    <v-row>
      <v-input>
        <v-text-field
          label="Email"
          placeholder="xxxxx@gmail.com"
          variant="outlined"
          clearable
        >
        </v-text-field>
      </v-input>
    </v-row>
  </v-container>

  <v-divider></v-divider>

  <v-container>
    <!-- v-data-table é o componente de tabela do Vuetify -->
    <!-- Define os cabeçalhos da tabela -->
    <!-- Define os dados que serão exibidos na tabela -->
    <!-- Adiciona uma sombra de elevação para o estilo -->
    <v-data-table 
    :headers="headers" 
    :items="clients" 
    item-key="id">

      <!--  Slot para o topo da tabela -->
      <template v-slot:top>
        <v-toolbar flat>
          <v-toolbar-title>Clientes</v-toolbar-title>
          <!-- Título da toolbar -->
        </v-toolbar>
      </template>
      <!-- Slot para as ações na tabela 
      <template v-slot:item.action="{ item }"> 
        >
      </template>-->
    </v-data-table>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        { title: 'ID', align: 'start', sortable: false, value: 'id' },
        { title: 'Nome', align: 'start', sortable: false, value: 'nome' },
        { title: 'Endereço', align: 'end', value: 'endereço' },
        { title: 'Número', align: 'end', value: 'numero' },
        { title: 'Telefone', align: 'end', value: 'telefone' },
        { title: 'Email', align: 'end', value: 'email' },
      ],
      clients: [],
    };
  },
  created() {
    this.loadClients();
  },
  methods: {
    async loadClients() {
      try {
        const response = await fetch('../../api/clientes.json');
        if (!response.ok) throw new Error('Erro ao carregar o arquivo JSON');
        const data = await response.json();

        // Log da estrutura dos dados recebidos
        console.log('Dados recebidos:', data);

        // Verifica se os dados têm a chave 'clientes' que é um array
        if (data.clientes && Array.isArray(data.clientes)) {
          this.clients = data.clientes;
        } else {
          console.error('Dados recebidos não contêm um array "clientes":', data);
        }
      } catch (error) {
        console.error('Erro ao carregar dados dos clientes:', error);
      }
    },
  },
};
</script>
