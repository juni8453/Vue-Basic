<template>
  <!-- 모달창 props 사용 (부모 데이터를 자식 컴포넌트로 전송 -->
  <!-- Component 활용 -->
  <Modal @closeModal="onModal = false"
      :products="products"
      :pickProductId="pickProductId"
      :onModal="onModal"
  />

  <div class="menu">
    <!-- key 는 인덱스로 자주 사용 -->
    <a v-for="(menu,i) in menus" :key="i"> {{ menu }} </a>
  </div>

  <!-- Component 활용 -->
  <Discount/>

  <!-- Component 활용 -->
  <!-- 이벤트 버블링으로 read only 를 해결할 수 있지만 특정 태그에 적용할 순 없다. -->
  <!-- 자식이 메세지를 송신하면 [@보낸 데이터] 이름 으로 수신받을 수 있다. -->
  <!-- 자식에 메세지를 송신하면 [갱신할 부모 데이터 = $event] 로 수신받을 수 있다. -->
  <Card @openModal="onModal = true; pickProductId = $event" v-for="(product, i) in products" :key="i"
      :product="product"
  />

</template>

<script>
import products from './products.js'
import Discount from "./components/Discount.vue"
import Modal from "./components/Modal.vue";
import Card from "./components/Card.vue"

export default {
  name: 'App',
  // 데이터 바구니 data(){} 로 실시간 자동 렌더링 데이터 바인딩 가능
  data() {
    return {
      products: products,
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
    Discount: Discount,
    Modal: Modal,
    Card: Card,
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
</style>
