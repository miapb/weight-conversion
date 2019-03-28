<template>
  <div id="app">
    <WeightConversion/>
  </div>
</template>

<script>
import WeightConversion from './components/WeightConversion.vue'

export default {
  name: 'app',
  components: {
    WeightConversion
  }
}
</script>

<style>

@font-face {
  font-family: 'Maven Pro';
  font-style: normal;
  font-weight: 400;
  src: local('Maven Pro Regular'), local('MavenPro-Regular'), url(https://fonts.gstatic.com/s/mavenpro/v11/7Au9p_AqnyWWAxW2Wk3GzWQI.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}

html {
  background-image: linear-gradient(to right bottom, #7b99c7, #49b1d5, #34c7c6, #72d6a2, #bfdc7d);
  background-repeat: no-repeat;
  height: 100%;
}

#app {
  font-family: 'Maven Pro', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
