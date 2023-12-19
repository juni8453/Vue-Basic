<template>
  <div>
    <img :src="product.image" class="room-img" alt="원룸 사진">
    <h4>{{ product.content }}</h4>
    <h4>{{ product.price }}만원</h4>
  </div>
</template>

<script>
export default {
  name: "Card.vue",
  props: {
    product: Object,
    pickProductId: Number,
  }
}
</script>

<style scoped>

</style>