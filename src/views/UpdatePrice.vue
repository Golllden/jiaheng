<template>
  <div class="calculate-tool">
    <div class="input-wrap">
      <router-link class="home-btn" to="/">返回</router-link>
      <div class="update-col">
        <label for="bullionPrice">條塊：</label>
        <input id="bullionPrice" type="number" v-model="newBullionPrice" />
      </div>
      <div class="update-col">
        <label for="goldPrice">飾金：</label>
        <input id="goldPrice" type="number" v-model="newGoldPrice" />
      </div>
      <div class="update-col">
        <label for="uRate">匯率：</label>
        <input id="uRate" type="number" v-model="newUsdtRate" />
      </div>
      <div class="update-col">
        <label for="key">鑰匙：</label>
        <input id="key" type="password" v-model="key" />
      </div>
      <!-- submit -->
      <button @click="validataSubmit" class="submit-btn">送出</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'updatePrice',
  data() {
    return {
      newBullionPrice: '',
      newGoldPrice: '',
      newUsdtRate: '',
      key: '',
    };
  },

  methods: {
    // 取得USDT匯率
    getUsdtRate: function () {
      let UsdApi = 'http://13.212.61.53:3000/api/price/usprice';

      axios
        .get(UsdApi)
        .then((response) => (this.newUsdtRate = response.data.usprice[0].usprice))
        .catch((error) => console.log(error));
    },

    // 取得飾金一錢多少
    getGoldPrice: function () {
      let golaAip = 'http://13.212.61.53:3000/api/price/goldprice';

      axios
        .get(golaAip)
        .then((response) => (this.newGoldPrice = response.data.goldprice[0].goldprice))
        .catch((error) => console.log(error));
    },
    // 取得條塊
    getGoldPriceB: function () {
      let golaAip = 'http://13.212.61.53:3000/api/price/goldpriceB';

      axios
        .get(golaAip)
        .then((response) => (this.newBullionPrice = response.data.goldpriceB[0].goldpriceB))
        .catch((error) => console.log(error));
    },

    validataSubmit() {
      if (!this.key) {
        alert('請輸入鑰匙密碼');
        return;
      }

      this.setNewPrice();
    },

    // call API修改
    setNewPrice: function () {
      let revisePriceApi = 'http://13.212.61.53:3000/api/price/priceset';

      axios
        .post(revisePriceApi, {
          usprice: this.newUsdtRate,
          goldprice: this.newGoldPrice,
          goldpriceB: this.newBullionPrice,
          key: this.key,
        })
        .then((response) => {
          alert('OK');
          this.$router.push({ path: '/' });
        })
        .catch((error) => {
          console.log(error);
          alert('失敗');
        });
    },
  },
  created() {
    this.getUsdtRate();
    this.getGoldPrice();
    this.getGoldPriceB();
  },
};
</script>

<style lang="scss" scoped>
.calculate-tool {
  width: 100vw;
  height: 95vh;

  // background-color: #9e7d56;
  background: linear-gradient(to right, rgb(255, 255, 255), #9e7d56);
  position: relative;
}

.input-wrap {
  box-sizing: border-box;
  border-radius: 5px;
  padding: 10px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -80%);
  border: 1px solid black;
  text-align: center;

  input {
    // padding: 2px;
    text-align: center;
    border-radius: 3px;
    padding: 3px 0;
  }
}

.update-col {
  font-size: 1.5rem;
  padding: 5px 5px;
}

.submit-btn {
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  background-color: #121212;
  cursor: pointer;
  color: white;
}

.home-btn {
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  background-color: #121212;
  cursor: pointer;
  color: white;
  text-decoration: none;
}
</style>
