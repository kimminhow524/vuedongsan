<template>
  <div>
    <transition name="fade">
     <Modal @closeModal="modalOn=false" :data="data" :oclick= "oclick" :modalOn="modalOn"/>
    </transition>

  <div class="menu">
    <a v-for="i in menus" :key="i">{{ i }}</a>
  </div>

  <Discount v-if="showDiscount==true" :discountper="discountper" />

  <button @click="priceSort()">가격순 정렬</button>
  <button v-if="back==true" @click="sortBack()">되돌리기</button>

  <Card @openModal="modalOn=true; oclick= $event" 
  :data="data" :oclick= "oclick" :modalOn="modalOn"/>
  </div>
</template>

<script>
import data from "../src/data.js";
import Discount from "../src/components/Discount.vue";
import Modal from "../src/components/Modal.vue";
import Card from "../src/components/Card.vue";
var timeup;
export default {
  name: "App",
  data() {
    return {
      showDiscount:true,
      back:false,
      dataOrg: [...data],
      oclick: 0,
      data: data,
      modalOn: false,
      policeNum: [0, 0, 0],
      menus: ["home", "product", "shop"],
      discountper:20,
    };
  },
  methods: {
    sortBack(){
      this.back=false;
      this.data = [...this.dataOrg];
    },
  priceSort(){
    this.back=true
    this.data.sort(function(a,b){
      return b.price-a.price
    })
  }
  },  
  created(){

  },
  
  mounted(){
     timeup=setInterval(()=>{
      this.discountper--;
    },1000)
  
  }, 
  updated(){
    if(this.discountper==0){
      clearInterval(timeup);
      this.showDiscount=false;
    }
  },
  components: {
    Discount: Discount,
    Modal:Modal,
    Card:Card,
  },
};
</script>

<style>
  @import "./assets/style.css";
</style>
