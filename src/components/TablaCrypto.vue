<template>
  <div>
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <button class="btn btn-outline-secondary" type="button" @click="refreshTable">Refrescar</button>
      </div>
      <input
        type="text"
        class="form-control"
        v-model="searchQuery"
        placeholder="Buscar criptomoneda"
      />
    </div>

    <ag-grid-vue
      v-if="cryptoData && cryptoData.data"
      :gridOptions="gridOptions"
      class="ag-theme-alpine"
      style="width: 100%; height: 400px;"
      :columnDefs="columnDefs"
      :rowData="filteredData"
      :domLayout="'autoHeight'"
    ></ag-grid-vue>

    <p v-else>Cargando...</p>
  </div>
</template>

<script>
import { AgGridVue } from "ag-grid-vue3";
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";

export default {
  components: {
    AgGridVue,
  },
  props: {
    cryptoData: Object,
  },
  data() {
    return {
      searchQuery: '',
      gridOptions: {
        pagination: true,
        sortable: true,
      },
      columnDefs: [
        { headerName: '#', valueGetter: 'node.rowIndex + 1', sortable: true },
        { headerName: 'Nombre', field: 'symbol', sortable: true },
        { headerName: 'Precio', field: 'quote.USD.price', sortable: true },
        { headerName: 'Capitalización', field: 'quote.USD.market_cap', sortable: true },
        { headerName: 'Suministro Máximo', field: 'max_supply', sortable: true },
        { headerName: 'Suministro Circulante', field: 'circulating_supply', sortable: true },
        { headerName: '1D %', field: 'quote.USD.percent_change_24h', sortable: true },
        { headerName: '30D %', field: 'quote.USD.percent_change_30d', sortable: true },
      ],
    };
  },
  computed: {
    filteredData() {
      if (!this.searchQuery) {
        return this.cryptoData.data;
      }
      return this.cryptoData.data.filter((crypto) =>
        `${crypto.symbol} ${crypto.name}`.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    refreshTable() {
      this.$forceUpdate();  // Refresca el componente
    },
  },
};
</script>

<style scoped>
.ag-theme-alpine {
  width: 100%;
  height: 400px;
}
</style>
