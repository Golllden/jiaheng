<template>
  <div class="calculate-tool-wrap">
    <div class="tool-header">{{ goldUnitText }}試算</div>
    <div class="input-grpup">
      <!-- 單位 -->
      <div class="input-col">
        <div class="input-title">
          單位:
          <!-- 單位選擇的選單, 單位欄位才要出現 -->
          <select v-model="calculateUnit">
            <option v-for="uint in unitList" :value="uint.eng">
              {{ uint.chinese }}
            </option>
          </select>
        </div>
        <div>
          <input class="input-content" type="number" v-model="inputWeight" placeholder="重量" />
        </div>
        <div class="remark-col"></div>
      </div>
      <!--  -->
      <div class="input-col">
        <div class="input-title">當日公告收價</div>
        <div class="display-content-warp">
          <div class="display-content">{{ displayPublicPriceByChoosenUnit }}</div>
        </div>
        <div class="remark-col"></div>
      </div>
      <div class="input-col">
        <div class="input-title">收購金額</div>
        <div class="display-content-warp">
          <div class="display-content">{{ calculatedAmount }}</div>
        </div>
        <div class="remark-col memo-text">已計耗損</div>
      </div>
      <div class="input-col">
        <div class="input-title">USDT換算</div>
        <div class="display-content-warp">
          <div class="display-content">{{ calculatedUsdt }}</div>
        </div>
        <div class="remark-col memo-text">匯率：{{ UsdtRate }}</div>
        <!-- <div class="usdt-rate">(匯率：{{ UsdtRate }})</div> -->
      </div>
    </div>
    <hr />
    <div class="submit-area">
      <span>例重: 一兩二錢三分四厘 = 12.34 (在框裡輸入重量後，點擊送出計算即可。)</span>
      <button @click="submitToCalculate" class="submit-btn">送出計算</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculateTool',
  props: {
    goldUnit: String,
    UsdtRate: Number,
    goldBasePrice: Number,
  },

  data() {
    return {
      inputWeight: '', //輸入重量
      calculatedAmount: '', //計算金額
      calculatedUsdt: '', //換算USDT
      unitList: [
        { eng: 'gram', chinese: '克' },
        { eng: 'liang', chinese: '兩' },
        { eng: 'penny', chinese: '錢' },
        { eng: 'kg', chinese: '公斤' },
      ],
      calculateUnit: 'penny',
    };
  },
  computed: {
    displayPublicPriceByChoosenUnit() {
      if (this.calculateUnit == 'gram') return (this.goldBasePrice / 3.75).toFixed(0);
      if (this.calculateUnit == 'liang') return (this.goldBasePrice * 10).toFixed(0);
      if (this.calculateUnit == 'kg') return ((this.goldBasePrice / 3.75) * 1000).toFixed(0);
      return this.goldBasePrice.toFixed(0);
    },

    // 單位的文字
    goldUnitText() {
      if (this.goldUnit == 'gold') {
        return '飾金';
      }

      return '黃金條塊';
    },
  },

  methods: {
    // 計算
    submitToCalculate: function () {
      if (this.inputWeight == 0 || this.inputWeight == '') {
        return;
      }

      // 飾金要另外再 *0.95
      let calculateAnswer = this.displayPublicPriceByChoosenUnit * this.inputWeight;
      this.calculatedAmount =
        this.goldUnit == 'gold' ? (calculateAnswer * 0.95).toFixed(0) : calculateAnswer.toFixed(0);

      this.calculatedUsdt = (this.calculatedAmount / this.UsdtRate).toFixed(2);

      alert('完成');
    },
  },
};
</script>

<style scoped lang="scss">
.calculate-tool-wrap {
  font-family: DFKai-sb;
  margin: 30px 0 30px 0;
}

.tool-header {
  text-align: center;
  padding: 5px 0;
  font-size: 1.25rem;
  font-weight: bold;
  color: white;
  background-color: #9e7d56;
}

.input-grpup {
  display: flex;
}

.input-col {
  flex: 1;
  display: flex;
  padding: 20px 2px;
  flex-direction: column;
  text-align: center;

  position: relative;
}

.input-title {
  padding: 5px 0;
  // color: #9e7d56;
  color: #121212;
  font-weight: 600;
  font-size: 1.1rem;
  height: 50%;
}

.input-content {
  font-weight: bold;
  width: 70%;
  height: 30px;
  border-radius: 5px;
  // color: #9e7d56;
  color: #121212;

  // border: 1px solid #9e7d56;
  border: 1px solid #121212;
  text-align: center;
  font-size: 1.25rem;
}

.display-content-warp {
  display: flex;
  justify-content: center;
}
.display-content {
  font-weight: bold;
  width: 92%;
  height: 20px;
  border-radius: 5px;
  padding: 5px 1px;
  color: #121212;
  border: 1px solid #121212;
  // border: 1px solid #9e7d56;
  text-align: center;
  font-size: 1.25rem;
  background-color: #fff;
}

.memo-text {
  color: #121212;
  font-weight: 600;
  font-size: 0.9rem;
}

hr {
  height: 2px;
  background-color: rgb(190, 190, 190);
}

select {
  // border: #9e7d56 1px solid;
  border: #121212 1px solid;
  border-radius: 5px;
  padding: 1px;
  font-weight: 600;
  // color: #9e7d56;
  color: #121212;
}

.submit-area {
  padding: 35px 10px;
  font-size: 1.15rem;
  font-weight: 600;
  color: #423d38;
}

.submit-btn {
  border: none;
  font-size: 1rem;
  padding: 5px 35px;
  background-color: rgb(230, 60, 60);
  border-radius: 5px;
  color: rgb(240, 240, 240);
  margin-left: 20px;
  cursor: pointer;

  &:hover {
    background-color: rgb(200, 20, 20);
  }
}

.remark-col {
  height: 50px;
}

@media screen and (max-width: 550px) {
}
</style>
