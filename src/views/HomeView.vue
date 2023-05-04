<template>
  <div class="home">
    <div class="calculate-banner"></div>

    <div class="main-content">
      <HomeDescription />
      <CalculateTool goldUnitText="黃金條塊" :UsdtRate="usdtRate" :goldBasePrice="bullionPrice" />
      <CalculateTool goldUnitText="飾金" :UsdtRate="usdtRate" :goldBasePrice="goldPrice" />
      <RemarkText />
    </div>
  </div>
</template>

<script>
import CalculateTool from '@/components/CalculateTool.vue';
import HomeDescription from '@/components/HomeDescription.vue';
import RemarkText from '@/components/RemarkText.vue';

import axios from 'axios';

export default {
  name: 'HomeView',

  components: {
    CalculateTool,
    HomeDescription,
    RemarkText,
  },

  data() {
    return {
      goldPrice: 0,
      bullionPrice: 7250, //
      usdtRate: 0,
    };
  },

  methods: {
    // 取得USDT匯率
    getUsdtRate: function () {
      let UsdApi = 'http://13.212.61.53:3000/api/price/usprice';

      axios
        .get(UsdApi)
        .then((response) => (this.usdtRate = response.data.usprice[0].usprice))
        .catch((error) => console.log(error));
    },

    // 取得飾金一錢多少
    getGoldPrice: function () {
      let golaAip = 'http://13.212.61.53:3000/api/price/goldprice';

      axios
        .get(golaAip)
        .then((response) => (this.goldPrice = response.data.goldprice[0].goldprice))
        .catch((error) => console.log(error));
    },
  },

  created() {
    this.getUsdtRate();
    this.getGoldPrice();
  },
};
</script>

<style lang="scss">
.calculate-banner {
  width: 100vw;
  height: 20vw;
  background-image: url('../assets/banner.jpg');
  background-position: center;
  background-size: cover;
}

.main-content {
  box-sizing: border-box;
  width: 100vw;
  padding: 50px 120px;
  background-color: #fff9f1;
}

@media screen and (max-width: 1050px) {
  .main-content {
    padding: 15px 0px;
  }
}
</style>
