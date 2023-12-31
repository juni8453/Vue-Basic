<template>

  <!-- 쌩 CSS 로 애니메이션 적용
  1. 시작 전 class 명
  2. 끝난 후 class 명
  3. 원할 떄 부착하고 싶은 위치(1번 뒤) 2번 class 명 부착
  4. :class = "{ 다이나믹하게 적용할 css class : 조건 }"
  <div class="start" :class="{ end : onModal }">
    <Modal @closeModal="onModal = false"
        :products="products"
        :pickProductId="pickProductId"
        :onModal="onModal"
    />
  </div>
  -->

  <transition name="fade">
    <!-- 모달창 props 사용 (부모 데이터를 자식 컴포넌트로 전송 -->
    <!-- Component 활용 -->
    <Modal @closeModal="onModal = false"
           :products="products"
           :pickProductId="pickProductId"
           :onModal="onModal"
    />
  </transition>

  <div class="menu">
    <!-- key 는 인덱스로 자주 사용 -->
    <a v-for="(menu,i) in menus" :key="i"> {{ menu }} </a>
  </div>

  <!-- Component 활용 -->
  <Discount v-if="showDiscount === true"/>

  <button @click="priceSortAsc">낮은 가격순 정렬</button>
  <button @click="priceSortDesc">높은 가격순 정렬</button>
  <button @click="sortBack">되돌리기</button>

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
      originProducts: [...products], // ...[array] 별개의 사본
      products: products,
      prices: [50, 60, 60],
      menus: ['Home', 'Products', 'About'],
      reportCounts: [0, 0, 0],
      onModal: false,
      pickProductId: 0,
      showDiscount: true,
    }
  },

  methods: {
    // 함수 만드는 공간
    // data() 의 값을 사용할 때 this 키워드 꼭 사용
    // 예시
    // increaseReportCount() {
    //   this.reportCount += 1;
    // },

    // 가격순 오름차순 정렬
    priceSortAsc() {
      this.products.sort(function (a, b) {
        return a.price - b.price;
      });
    },

    // 가격순 내림차순 정렬
    priceSortDesc() {
      this.products.sort(function (a, b) {
        return b.price - a.price;
      });
    },

    // 정렬 되돌리기
    sortBack() {
      this.products = [...this.originProducts];
    }
  },

  // 라이프사이클 훅으로 UI 개발
  // beforeCreate(), created(), beforeMount(), mounted()
  // beforeUpdate(), updated(), beforeUnmount(), unmounted() 등
  // function() {...} 로는 바깥의 데이터를 this 로 사용불가, 애로우 함수 사용
  // 서버에 데이터를 요청할 때 라이프사이클 훅을 사용한다. (created() / mounted() 많이 사용)
  mounted() {
    // 마운트 2초 이후 Discount 배너 사라지도록 하는 예시
    // setTimeout(() => {
    //   this.showDiscount = false;
    // }, 2000);
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

/*
쌩 CSS 애니메이션 적용
*/
.start {
  opacity: 0;
  transition: all 1s;
}

.end {
  opacity: 1;
}

/*
<transition> 으로 애니메이션 적용
작명-enter-from / active / to 로 정의
*/
.fade-enter-from { /* 시작 스타일 */
  opacity: 0;
}

.fade-enter-active { /* 적용할 애니메이션 */
  transition: all 1s;
}

.face-enter-to { /* 끝 스타일 */
  opacity: 1;
}

/* 퇴장 애니메이션 */
.fade-leave-from { /* 시작 스타일 */
  opacity: 1;
}

.fade-leave-active { /* 적용할 애니메이션 */
  transition: all 1s;
}

.face-leave-to { /* 끝 스타일 */
  opacity: 0;
}

</style>
