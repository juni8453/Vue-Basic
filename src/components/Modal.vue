<template>
  <div class="black-bg" v-if="onModal === true">
    <div class="white-bg">
      <h4>{{ products[pickProductId].title }}</h4>
      <img :src="products[pickProductId].image" class="room-img" alt="원룸 사진">
      <p>{{ products[pickProductId].content }}</p>
      <p>{{ products[pickProductId].price }}</p>
      <button @click="$emit('closeModal')">창닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal.vue",
  // 부모(App.vue) 데이터를 자식 컴포넌트에서 사용하고 싶다면 props 등록
  // 주의) props 는 read-only 이기 때문에 수정 불가
  props: {
    products: Array,
    pickProductId: Number,
    onModal: Boolean,
  },
  data() {
    return {

    }
  },
}
</script>

<style scoped>
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