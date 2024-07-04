<template>

<v-container fluid class="custom-cont">
        <div>
          <v-row class="d-flex align-center">
            <h2>Dashboard</h2>
          </v-row>
          <v-row class="d-flex justify-space-between align-center">
            <h3 class="circle">Cadastro</h3>
          </v-row>
        </div>

        <v-divider style="margin-top: 20px"></v-divider>
      </v-container>


</template>

<script>
export default {
    
}
</script>

<style scoped>
.space {
  padding: 10px;
}

.circle {
  display: inline-block;
  position: relative;
  padding: 10px 15px;
  margin: 10px;
  background-color: purple;
  color: white;
  border-radius: 20px;
}

.custom-cont {
  width: 100%;
  padding: 30px;
  margin-left: 10px;
  margin-right: 10px;
}
</style>