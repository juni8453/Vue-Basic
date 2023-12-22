<template>
  <div class="discount">
    <h4>지금 결제하면 {{discountPercent}}% 할인</h4>
  </div>

</template>

<script>
export default {
  name: "Discount.vue",
  data() {
    return {
      discountPercent: 30,
    }
  },

  mounted() {
    setInterval(() => {
      if (this.discountPercent > 0) {
        this.discountPercent -= 1;
      }
    }, 1000);
  }
}
</script>

<style scoped>

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

</style>