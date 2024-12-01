<script>
import axios from 'axios'
import TablaCrypto from './components/TablaCrypto.vue';
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    TablaCrypto,
    Navbar
  },
  data() {
    return {
      info: null, 
    };
  },
  mounted() {
    axios
  .get('https://cors-anywhere.herokuapp.com/https://pro-api.coinmarketcap.com/v1/cryptocurrency/listings/latest', {
    headers: {
      'X-CMC_PRO_API_KEY': '1276dec7-5445-4bc4-9029-a052f3c160ee', 

    },
    params: {
      limit: 100,
      sort: 'market_cap',
    },
  })
  .then((response) => {
    this.info = response.data;
  })
  .catch((error) => {
    console.error(error);
  });

  },
};

</script>

<template>
 <Navbar />
<div class="d-flex justify-content-center">
  <div class="container mt-4 pt-5">
    <h1 class="text-center">100 criptomonedas con mayor capitalización de mercado</h1>
  <TablaCrypto :cryptoData="info"/>
  </div>
</div>
</template>


<style scoped>


</style>


