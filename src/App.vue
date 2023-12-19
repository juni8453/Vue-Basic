<template>

  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h4>XX 원룸</h4>
    <p>{{ price1 }}만원</p>
  </div>
  <div>
    <h4>XX 원룸</h4>
    <p>{{ price2 }}만원</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  // 데이터 바구니 data(){} 로 실시간 자동 렌더링 데이터 바인딩 가능
  data() {
    return {
      price1: 60,
      price2: 70,
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
