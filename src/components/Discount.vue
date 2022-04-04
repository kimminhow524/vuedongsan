<template>
  <div class="disCount">
    <h4>지금 결제하면 {{discountper}}%할인</h4>
  </div>
</template>

<script>
export default {
  name: "the-Discount",
  props:{
    discountper:Number
  }
};
</script>

<style></style>
