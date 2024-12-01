<template>
  <div>
    <table
      v-if="cryptoData && cryptoData.data"
      id="cryptoTable"
      class="table table-bordered table-striped table-hover"
    >
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nombre</th>
          <th scope="col">Precio</th>
          <th scope="col">Capitalización</th>
          <th scope="col">Suministro Máximo</th>
          <th scope="col">Suministro Circulante</th>
          <th scope="col">1D %</th>
          <th scope="col">30D %</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(crypto, index) in cryptoData.data" :key="crypto.id">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ crypto.symbol }}</td>
          <td>{{ crypto.quote.USD.price | currency }}</td>
          <td>{{ crypto.quote.USD.market_cap | currency }}</td>
          <td>{{ crypto.max_supply | currency }}</td>
          <td>{{ crypto.circulating_supply | currency }}</td>
          <td>{{ crypto.quote.USD.percent_change_24h }}%</td>
          <td>{{ crypto.quote.USD.percent_change_30d }}%</td>
        </tr>
      </tbody>
    </table>
    <p v-else>Cargando...</p>
  </div>
</template>

<script>
import $ from 'jquery';
import 'datatables.net-bs5';

export default {
  props: {
    cryptoData: Object,
  },
  data() {
    return {
      searchQuery: '',
    };
  },
  filters: {
    
    currency(value) {
      if (value === null || value === undefined) return '$0.00';
      return '$' + value.toFixed(2).replace(/\d(?=(\d{3})+\.)/g, '$&,');
    },
  },
  watch: {
    searchQuery(newQuery) {
      
      $('#cryptoTable').DataTable().search(newQuery).draw();
    },
  },
  mounted() {
    
    this.$nextTick(() => {
      $('#cryptoTable').DataTable();
    });
  },
  beforeDestroy() {
    if ($.fn.dataTable.isDataTable('#cryptoTable')) {
      $('#cryptoTable').DataTable().destroy();
    }
  },
};
</script>

<style scoped>

.table {
  margin-top: 5px;
  width: 100%;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.table th, .table td {
  text-align: center;
  vertical-align: middle;
}

.table thead {
  background-color: #4275af;
  color: white;
  font-weight: bold;
}

.table tbody tr:hover {
  background-color: #f1f1f1;
}

.table-bordered {
  border: 1px solid #ddd;
}

.table-striped tbody tr:nth-child(odd) {
  background-color: #f9f9f9;
}

.table-hover tbody tr:hover {
  background-color: #e9ecef;
}
</style>
