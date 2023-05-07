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
        <input id="key" type="number" v-model="key" />
      </div>
      <!-- submit -->
      <button @click="submitUpdate" class="submit-btn">送出</button>
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
    submitUpdate() {
      if (this.newUsdtRate <= 0 || !this.newUsdtRate) {
        alert('操作有誤');
        return;
      }
      if (this.newGoldPrice <= 0 || !this.newGoldPrice) {
        alert('操作有誤');
        return;
      }
      if (this.newBullionPrice <= 0 || !this.newBullionPrice) {
        alert('操作有誤');
        return;
      }

      if (this.key != '0897') {
        alert('操作有誤');
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
        })
        .then((response) => {
          alert('OK');
          this.$router.push({ path: '/' });
        })
        .catch((error) => {
          console.log(error);
        });
    },
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
