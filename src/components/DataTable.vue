<template>
  <v-data-table
    class="table"
    :headers="headers"
    :items="users"
    :rows-per-page-items="[10, 25]">
    <template slot="items" slot-scope="props">
      <td>{{ props.item.startDate }}</td>
      <td>{{ props.item.weekAyer }}</td>
      <td>{{ props.item.nBonus }}</td>
      <td>{{ props.item.totalSale }}</td>
      <td>{{ props.item.amountBonus }}</td>
      <td>{{ props.item.nRedeem }}</td>
      <td>{{ props.item.amountRedeem }}</td>
      <td>{{ props.item.nExpiration }}</td>
      <td>{{ props.item.amountExpiration }}</td>
      <td>{{ props.item.amountBalance }}</td>
    </template>
  </v-data-table>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      headers: [
        {
          text: 'Fecha inicio',
          value: 'startDate',
          align: 'left',
          sortable: true
        },
        {
          text: 'Semana Año',
          value: 'weekAyer',
          align: 'left',
          sortable: true
        },
        {
          text: '# TransBonificación',
          value: 'nBonus',
          align: 'left',
          sortable: true
        },
        {
          text: 'Ventas totales',
          value: 'totalSale',
          align: 'left',
          sortable: true
        },
        {
          text: 'Monto boni',
          value: 'amountBonus',
          align: 'left',
          sortable: true
        },
        {
          text: '# TransRedencion',
          value: 'nRedeem',
          align: 'left',
          sortable: true
        },
         {
          text: 'Monto Redencion',
          value: 'amountRedeem',
          align: 'left',
          sortable: true
        },
         {
          text: '# TrandExpirado',
          value: 'nExpiration',
          align: 'left',
          sortable: true
        },
         {
          text: 'Monto expirado',
          value: 'amountExpiration',
          align: 'left',
          sortable: true
        },
         {
          text: 'Saldo disponible',
          value: 'amountBalance',
          align: 'left',
          sortable: true
        }
      ]
    }
  },
  methods: {
  },
  created() {
    const vm = this;
    vm.axios.get('http://localhost:4422/addTransaction').then(response => {
      var result = response && response.data;
      vm.users = result.data;
    });
  }
}
</script>

<style>
  .table {
    border-radius: 3px;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.125);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.21);
    background-color: transparent;
  }
</style>
