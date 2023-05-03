<template>
  <div class="calculate-tool-wrap">
    <div class="tool-header">
      <h3>條塊</h3>
    </div>
    <div class="input-area">
      <input type="text" />
    </div>
    <hr />
    <p>例重: 一兩二兩</p>
    <button>計算</button>
  </div>
</template>

<script>
export default {
  name: 'CalculateTool',
  // props: {
  //   msg: String,
  // },
};
</script>

<style scoped lang="scss">
.calculate-tool-wrap {
  padding: 10px 0;
  border: 2px solid rgb(0, 0, 0);
  margin-top: 25px;
}

hr {
  height: 3px;
  background-color: rgb(160, 160, 160);
}
</style>
