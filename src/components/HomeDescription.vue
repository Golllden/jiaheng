<template>
  <!-- 試算說明文字 -->
  <div class="calculate-discription">
    <div class="discription-header">線上試算說明</div>
    <div class="discription-text">
      <ul>
        <li>•實際兌換金額依現場實際檢驗後，現場實際秤重報價為主。</li>
        <li>•黃金回收價格每日更新，請依<span class="current-time">目前時間</span>為主，試算金額僅供當日參考。</li>
        <li class="current-time">目前時間：{{ displayCurrentTime }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeDescription',

  data() {
    return {
      displayCurrentTime: '',
    };
  },

  methods: {
    getCurTime() {
      let time = new Date();

      let year = time.getFullYear();
      let month = time.getMonth() + 1;
      let date = time.getDate();
      let hour = time.getHours();
      let mins = time.getMinutes();
      this.displayCurrentTime = year + '/' + month + '/' + date + '  ' + hour + ':' + mins;
    },
  },

  created() {
    this.getCurTime();
  },
};
</script>

<style lang="scss">
.calculate-discription {
  text-align: center;
  font-family: DFKai-sb;
}

.discription-header {
  padding: 5px 0;
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
  background-color: #9e7d56;
}

.discription-text {
  width: 100%;
  color: #8f6f4a;
  font-weight: bolder;
  font-size: 1.15rem;
  background-color: #f0e3d4;

  ul {
    list-style: none;
    margin: 0;
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
