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
      <v-col  cols="2">
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
</template>

<script></script>
