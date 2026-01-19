<template>
  <div id="app">
    <!-- Introduction Portfolio on Top -->
    <IntroSection />
    
    <!-- Vue Components Below -->
    <div class="vue-components-section">
      <h1>Personal Profile and Fruits</h1>
      <food-item/>
      <food-item2/>
    </div>
  </div>
</template>

<script>
import IntroSection from './components/IntroSection.vue';
import FoodItem from './components/FoodItem.vue';
import FoodItem2 from './components/FoodItem2.vue';

export default {
  name: 'App',
  components: {
    IntroSection,
    FoodItem,
    FoodItem2
  }
};
</script>

<style>
#app {
  width: 100%;
}

.vue-components-section {
  padding: 40px 20px;
  text-align: center;
  background-color: var(--bg-color, #f5f0ff);
}

.vue-components-section h1 {
  margin-bottom: 30px;
  color: var(--text-color, #2d1b4e);
}
</style>

