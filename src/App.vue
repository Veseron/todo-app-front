<template>
  <div id="app">
    <Header/>
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header'

export default {
  components: {
    Header
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
}

body {
  font-size: 18px;
}

h1 {
  margin: 10px 0;
}

h2 {
  margin: 8px 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.container {
  max-width: 1200px;
  padding: 0 15px;
  margin: 0 auto;
}
</style>
