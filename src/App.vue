<template>
  <!-- 모달창 -->
  <div class="black-bg" v-if="onModal === true">
    <div class="white-bg">
      <h4>{{ products[pickProductId].title }}</h4>
      <img :src="products[pickProductId].image" class="room-img" alt="원룸 사진">
      <p>{{ products[pickProductId].content }}</p>
      <p>{{ products[pickProductId].price }}</p>
      <button @click="onModal = false">창 닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- key 는 인덱스로 자주 사용 -->
    <a v-for="(menu,i) in menus" :key="i"> {{ menu }} </a>
  </div>

  <div v-for="(product,i) in products" :key="i">
    <!-- 속성에 바인딩 시 콜론 기억 -->
    <img :src="product.image" class="room-img" alt="원룸 사진">
    <h4 @click="onModal = true; pickProductId = i">{{ product.title }}</h4>
    <h4>{{ product.content }}</h4>
    <h4>{{ product.price }}만원</h4>
  </div>
</template>

<script>
import roomProducts from './products.js'

export default {
  name: 'App',
  // 데이터 바구니 data(){} 로 실시간 자동 렌더링 데이터 바인딩 가능
  data() {
    return {
      products: roomProducts,
      prices: [50, 60, 60],
      menus: ['Home', 'Products', 'About'],
      reportCounts: [0, 0, 0],
      onModal: false,
      pickProductId: 0,
    }
  },

  methods: {
    // 함수 만드는 공간
    // data() 의 값을 사용할 때 this 키워드 꼭 사용
    // 예시
    // increaseReportCount() {
    //   this.reportCount += 1;
    // },
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
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
 
/* 모달창 디자인 */
body {
  margin: 0
}

div {
  box-sizing: border-box
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
