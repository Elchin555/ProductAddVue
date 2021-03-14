<template>
  
     <div class="row product-container">
      <product v-for="(pro,key) in productList" :key="key">
        <img class="card-img-top"
        :src="pro.selectedImage"
         alt="Card image cap">
        <div class="card-body">
          <h5 class="card-title">{{pro.title}}</h5>
          <small>
            <strong>Adet : </strong> {{pro.count}}
          </small>
          <br>
          <small>
            <strong>Fiyat : </strong> {{pro.price}}
          </small>
          <br>
          <small>
            <strong>Tutar : </strong> {{pro.total}}
          </small>
      </div>
      </product>
    </div>
  
</template>

<script>
import { eventBus } from '../main'
import product from "./product"
export default {
  components:{product},
  data(){
    return{
      productList:[]
    }
  },
  created(){
    eventBus.$on("sendData",(e)=>{
      if(this.productList.length<2){
        this.productList.push(e)
        eventBus.$emit("sendProgressBarData",this.productList.length)

      }
      else{
        alert("UJe gijdedin maksiumum 2 dene gondere bilersen")
      }
    })
  },
  
}
</script>