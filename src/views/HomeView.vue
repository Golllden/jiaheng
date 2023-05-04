<template>
  <div class="home">
    <div class="calculate-banner"></div>

    <div class="main-content">
      <HomeDescription />
      <CalculateTool goldUnitText="黃金條塊" :UsdtRate="usdtRate" :goldBasePrice="bullionPrice" />
      <CalculateTool goldUnitText="飾金" :UsdtRate="usdtRate" :goldBasePrice="goldPrice" />
      <RemarkText />
    </div>
  </div>
</template>

<script>
import CalculateTool from '@/components/CalculateTool.vue';
import HomeDescription from '@/components/HomeDescription.vue';
import RemarkText from '@/components/RemarkText.vue';

export default {
  name: 'HomeView',

  components: {
    CalculateTool,
    HomeDescription,
    RemarkText,
  },

  data() {
    return {
      goldPrice: 7000,
      bullionPrice: 7250,
      usdtRate: 31.1,
    };
  },

  methods: {
    test() {
      console.log('hell world');
    },
  },
};
</script>

<style lang="scss">
.calculate-banner {
  width: 100vw;
  height: 20vw;
  background-image: url('../assets/banner.jpg');
  background-position: center;
  background-size: cover;
}

.main-content {
  box-sizing: border-box;
  width: 100vw;
  padding: 50px 120px;
  background-color: #fff9f1;
}

@media screen and (max-width: 1050px) {
  .main-content {
    padding: 15px 0px;
  }
}
</style>
