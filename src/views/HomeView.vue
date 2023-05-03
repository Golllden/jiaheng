<template>
  <div class="home">
    <div class="calculate-banner"></div>

    <div class="main-content">
      <HomeDescription />
      <CalculateTool />
      <CalculateTool />
    </div>
  </div>
</template>

<script>
import CalculateTool from '@/components/CalculateTool.vue';
import HomeDescription from '@/components/HomeDescription.vue';

export default {
  name: 'HomeView',

  components: {
    CalculateTool,
    HomeDescription,
  },

  data() {
    return {
      name: 'bbb',
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

@media screen and (max-width: 768px) {
  .main-content {
    padding: 15px 0px;
  }
}

// @media screen and (min-width: 1024px) {
// }

// @media screen and (min-width: 1200px) {
// }

// @media screen and (min-width: 768px) and (max-width: 979px) {
// }

// @media screen and (max-width: 767px) {
// }

// @media screen and (max-device-width: 480px) {
// }
</style>
