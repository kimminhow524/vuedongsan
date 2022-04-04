<template>
 <div class="black-bg" v-if="modalOn == true">
    <div class="white-bg">
      <img :src="data[oclick].image" class="room-img" style="width:100%"/>
      <p>{{ data[oclick].content }}</p>
      <input v-model="month"/>
      <p>{{month}} 개월 선택됨 {{ data[oclick].price *month}}</p>

       <button @click="$emit('closeModal')">close</button> 
    </div>
  </div>
</template>
<script>
export default {
  name: "the-Modal",
  data(){
    return{
      month: 1 ,
    }
  },
  watch:{
    month(a){
      if (isNaN(a)==true){
        this.month=1
        alert("ㄴㄴㄴㄴ")
      }
    }
  },
  
  props:{
    data:Array,
  modalOn:Boolean,
  oclick:Number,
  },
  
  beforeUpdate(){
    if(this.month==2){
      alert("콩까지마");
      this.month=3;
    }

  },
  methods:{

  }
};
</script>

<style></style>
