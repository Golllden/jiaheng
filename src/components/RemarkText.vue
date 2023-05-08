<template>
  <div class="remark-wrap">
    <h5>
      備註
      <span @click="openUpdatePage">:</span>
    </h5>
    <!-- <router-link to="/UpdatePrice">:</router-link> -->
    <ul>
      <li v-for="(text, index) in remarkTextList">
        {{ text }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'RemarkText',
  data() {
    return {
      remarkTextList: [
        '飾金於加工時常使用黏著劑等物加工，因此回收過程中，就需要再進行熔製及除膠，過程中會再有耗損，扣除飾金回收耗損後的實際價格，通常為飾金本身重量乘上0.88~0.95不等，我司則以*0.95計算收購價格。',
        '黃金的重量單位分為(兩、錢、克、公斤)，採十進位。',
        '飾金舉凡為戒指、項鍊、手鍊、耳環、領帶夾、婚套等；條塊舉凡景(錦)福、中央信託局瑞士條塊、金龍條塊、煌隆條塊...等',
        '以上表格數據僅供參考，可在您得知當日回收金價後，在金價試算旁輸入金重後送出計算，即可得知本公司回收金額，其餘欄位不需異動。',
      ],
      counter: 0,
    };
  },
  methods: {
    openUpdatePage() {
      this.counter++;

      if (this.counter == 5) {
        this.$router.push({ path: 'UpdatePrice' });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.remark-wrap {
  padding: 15px 30px;
  width: 100%;
  border: 1px solid rgb(75, 75, 75);
  box-sizing: border-box;
  color: #423d38;
  font-weight: bold;
  font-family: DFKai-sb;
  font-size: 0.85rem;

  h5 {
    padding: 10px 0;
    font-size: 1.25rem;
  }

  li {
    padding: 6px 0;
    font-size: 1.25rem;
    letter-spacing: 2px;
  }

  a {
    text-decoration: none;
    color: none;
    cursor: none;
  }
}
</style>
