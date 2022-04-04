<template>
 <div v-for="(a, i) in data" :key="i">
    <img :src="data[i].image" class="room-img" style="width:100%"/>
    <h4 @click="$emit('openModal',data[i].id)">
      <span>
        {{ data[i].title }}
      </span>
    </h4>
    <p>{{ data[i].price }}만원</p>
  </div>
</template>
<script>
export default {
  name: "the-Card",
  props:{data:Array,
  modalOn:Boolean,
  oclick:Number,
  }
};
</script>

<style></style>
