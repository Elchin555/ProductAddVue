<template>
   <div class="row">
      <div class="card offset-2 col-md-3">
        <div class="card-body tex-center d-flex align-items-center flex-column">
          <img height="128" class="img-responsive text-center mb-3"
               :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
          <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
          <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">add Image</button>
        </div>
      </div>
      <div class="col-md-5">
        <div class="col-md-11 card">
          <div class="card-body">
            <div class="form-group">
              <label>Title</label>
              <input type="text" class="form-control" placeholder="Product Name" v-model="product.title">
            </div>
            <div class="row">
              <div class="form-group col-md-6">
                <label>Count</label>
                <input type="text" class="form-control" placeholder="Count" v-model="product.count">
              </div>
              <div class="form-group col-md-6">
                <label>Price</label>
                <input type="text" class="form-control" placeholder="Price" v-model="product.price">
              </div>
            </div>
            <button class="btn btn-outline-info btn-block" @click="addProduct">Add!</button >
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import {eventBus} from "../main"
export default {
  data(){
    return{
      product:{
        title:null,
        count:null,
        price:null,
        total:null,
        selectedImage:null,
      },
      
    }
  },
  methods: {
      onChange(e) {
        const file = e.target.files[0];
        this.product.selectedImage = URL.createObjectURL(file);
      },
    
      addProduct(){
        this.product.total=this.product.price * this.product.count
        eventBus.$emit("sendData",this.product);
        this.product={
        title:null,
        count:null,
        price:null,
        total:null,
        selectedImage:null,
      }
      },
   
    }
}
</script>