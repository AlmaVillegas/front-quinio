<template>
  <v-card >
    <v-card-text >
      <line-chart :data="data" xtitle="Time" ytitle="Bonificaciones Diarias " :dataset="{borderWidth: 3}"/>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
       data: {
        semana:'',
        bonus: ''
        }
    }
  }, 
  created() {
    const vm = this;
    vm.axios.get('http://localhost:4422/TransactionbonusDaily').then(response => {
      let result = response && response.data;
      vm.data.semana = result.data.Semana;
      vm.data.bonus = result.data.bonus;
      console.log(vm.data)
    });
  }
  
}
</script>

<style>
  .card {
    border-radius: 3px;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.125);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.21);
    background-color: transparent;
  }
</style>
