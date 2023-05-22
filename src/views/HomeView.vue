<template>
  <div class="home">
    <div class="calculate-banner"></div>

    <div class="main-content">
      <HomeDescription />
      <CalculateTool goldUnit="bullion" :UsdtRate="usdtRate" :goldBasePrice="bullionPrice" />
      <CalculateTool goldUnit="gold" :UsdtRate="usdtRate" :goldBasePrice="goldPrice" />
      <RemarkText />
      <div class="btn-wrap">
        <button class="home-btn" @click="goHome">返回首頁</button>
      </div>
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
      bullionPrice: 0, //
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
    // 取得條塊
    getGoldPriceB: function () {
      let golaAip = 'http://13.212.61.53:3000/api/price/goldpriceB';

      axios
        .get(golaAip)
        .then((response) => (this.bullionPrice = response.data.goldpriceB[0].goldpriceB))
        .catch((error) => console.log(error));
    },

    // 返回首頁
    goHome() {
      console.log('home');
      location.href = 'https://jh-gold.com';
      // https://jh-gold.com/
    },
  },

  created() {
    this.getUsdtRate();
    this.getGoldPrice();
    this.getGoldPriceB();
  },
};
</script>

<style lang="scss">
.calculate-banner {
  width: 100vw;
  height: 25vw;
  background-image: url('../assets/banner.png');
  background-position: center;
  background-size: cover;
}

.main-content {
  box-sizing: border-box;
  width: 100vw;
  padding: 50px 120px;
  background-color: #fff9f1;
}

.btn-wrap {
  margin-top: 20px;
  text-align: center;
}

.home-btn {
  width: 200px;
  padding: 8px;
  border-radius: 5px;
  background-color: #9e7d56;
  color: white;
  font-weight: bolder;
}

@media screen and (max-width: 1050px) {
  .main-content {
    padding: 15px 0px;
  }
}
</style>
