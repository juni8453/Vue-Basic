<template>
  <div>
    <img :src="product.image" class="room-img" alt="원룸 사진">
    <!-- <h4 @click="onModal = true">{{ product.title }}</h4> -->
    <!-- props 는 read-only 이기 때문에 수정 불가 -->
    <!-- 따라서 이벤트 리스너를 통해 자식 컴포넌트에서 부모 컴포넌트의 이벤트를 전달받아 데이터를 수정하는 방법 사용 가능 -->
    <!-- 즉, 자식인 Card 에서 부모인 App 의 onModal 데이터를 true 로 변경하고 싶은 지금 상황에서 사용 가능 -->
    <!-- $emit('작명', 보내고 싶은 데이터(생략가능) -->
    <h4 @click="$emit('openModal', product.id)">{{ product.title }}</h4>
    <h4>{{ product.content }}</h4>
    <h4>{{ product.price }}만원</h4>
  </div>
</template>

<script>
export default {
  name: "Card.vue",
  props: {
    product: Object,
  }
}
</script>

<style scoped>

</style>