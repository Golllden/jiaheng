<template>
  <!-- 試算說明文字 -->
  <div class="calculate-discription">
    <div class="discription-header">
      <h2>線上試算說明</h2>
    </div>
    <div class="discription-text">
      <ul>
        <li>• 實際兌換金額依現場實際檢驗後，現場實際秤重報價為主。</li>
        <li>• 黃金回收價格每日更新，請依<span class="current-time">目前時間</span>為主，試算金額僅供當日參考。</li>
        <span class="current-time">目前時間：2023/05/10 18:00 ....</span>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeDescription',
};
</script>

<style lang="scss">
.calculate-discription {
  text-align: center;
}

.discription-header {
  padding: 12px 0;
  color: rgb(245, 245, 245);
  font-weight: bold;
  font-size: 1.3rem;
  letter-spacing: 3px;
  background-color: #9e7d56;
}

.discription-text {
  color: #8f6f4a;
  font-weight: bolder;
  font-size: 1.15rem;
  background-color: #f0e3d4;
  padding: 30px 0;

  ul {
    list-style: none;
    margin: 0;
    // padding: 20px;
  }

  li {
    padding: 8px 0;
    letter-spacing: 1px;
  }
}

.current-time {
  color: rgb(230, 85, 85);
}
</style>
