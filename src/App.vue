<template>

  <!-- 모달창 -->
  <div class="black-bg" v-if="onModal == true">
    <div class="white-bg">
      <h4>상세 페이지임</h4>
      <p>상세 페이지 내용임</p>
      <button @click="onModal = false">창 닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- key 는 인덱스로 자주 사용 -->
    <a v-for="(menu,i) in menus" :key="i"> {{ menu }} </a>
  </div>

  <div>
    <img src="./assets/room0.jpg" class="room-img">
    <h4 @click="onModal = true">{{ products[0] }}</h4>
    <p>{{ prices[0] }} 만원</p>
    <button @click="reportCounts[0]++">허위매물 신고</button> 
    <span> 신고수: {{ reportCounts[0] }}</span>
  </div>

  <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4>{{ products[1] }}</h4>
    <p>{{ prices[1] }} 만원</p>
    <button @click="reportCounts[1]++">허위매물 신고</button> 
    <span> 신고수: {{ reportCounts[1] }}</span>
  </div>

  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4>{{ products[2] }}</h4>
    <p>{{ prices[2] }} 만원</p>
    <button @click="reportCounts[2]++">허위매물 신고</button> 
    <span> 신고수: {{ reportCounts[2] }}</span>
  </div>

</template>

<script>

export default {
  name: 'App',
  // 데이터 바구니 data(){} 로 실시간 자동 렌더링 데이터 바인딩 가능
  data() {
    return {
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      prices: [50, 60, 60],
      menus: ['Home', 'Products', 'About'],
      reportCounts: [0, 0, 0],
      onModal: false,
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
  background: rgba(0, 0, 0, 0, 5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

</style>
