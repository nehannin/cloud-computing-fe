<script setup>
import SentimentAnalysis from './components/SentimentAnalysis.vue';
</script>

<template>
  <div id="app">
    <SentimentAnalysis />
  </div>
</template>

<script>
import SentimentAnalysis from './components/SentimentAnalysis.vue';

export default {
  name: 'App',
  components: {
    SentimentAnalysis
  }
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
}
</style>
