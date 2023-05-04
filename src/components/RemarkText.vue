<template>
  <div class="remark-wrap">
    <h5>備註:</h5>
    <ul>
      <li v-for="text in remarkTextList">
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
        '黃金的重量單位分為(兩、錢、克、公斤)，採十進位。',
        '飾金舉凡為戒指、項鍊、手鍊、耳環、領帶夾、婚套等；條塊舉凡景(錦)福、中央信託局瑞士條塊、金龍條塊、煌隆條塊...等',
        '以上表格數據僅供參考，可在您得知當日回收金價後，在金價試算旁輸入金重後送出計算，即可得知本公司回收金額，其餘欄位不需異動。',
        '本公司是以_______________統一報價。',
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.remark-wrap {
  padding: 15px 30px;
  width: 100%;
  border: 1px solid grey;
  box-sizing: border-box;
  color: #9e7d56;
  font-weight: bold;
  font-family: DFKai-sb;
  font-size: 0.85rem;

  h5 {
    padding: 10px 0;
  }

  li {
    padding: 6px 0;
  }
}
</style>
