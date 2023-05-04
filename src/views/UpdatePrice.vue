<template>
  <div class="calculate-tool">
    <div class="input-wrap">
      <div class="update-col">
        <label for="goldPrice">條塊：</label>
        <input id="goldPrice" type="number" />
      </div>
      <div class="update-col">
        <label for="bullionPrice">飾金：</label>
        <input id="bullionPrice" type="number" />
      </div>
      <div class="update-col">
        <label for="uRate">匯率：</label>
        <input id="uRate" type="number" />
      </div>
      <div class="update-col">
        <label for="key">鑰匙：</label>
        <input id="key" type="number" />
      </div>
      <!-- submit -->
      <button class="submit-btn">送出</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'updatePrice',
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.calculate-tool {
  width: 100vw;
  height: 95vh;
  background-color: #9e7d56;
  position: relative;
}

.input-wrap {
  border-radius: 5px;
  padding: 20px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -80%);
  border: 1px solid black;
  text-align: center;

  input {
    // padding: 2px;
    border-radius: 3px;
    padding: 5px 0;
  }
}

.update-col {
  font-size: 1.5rem;
  padding: 10px 50px;
}

.submit-btn {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
  background-color: #121212;
  cursor: pointer;
  color: white;
}
</style>
