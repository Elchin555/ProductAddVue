<template>
  <div class="container">
    <h1 class="text-center">Ürün Ekleme Uygulaması</h1>
    <hr>
   <newProduct></newProduct>
    <br><br>
   <progressBar></progressBar>
   
    
    <br><br>
    <h3 class="text-center">Product List</h3>
    <hr>
   <products></products>
  </div>


</template>

<script>
import newProduct from "./components/newProduct";
import progressBar from "./components/progressBar";
import products from "./components/products";
  export default {
    components:{
      newProduct,progressBar,products
    },
    data() {
      return {
        imageList: [],
        product : {
            selectedImage: null
        }
      }
    },
    
  }
</script>

<style>
  body {
    background-color: aliceblue;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .card{
    margin-right: 5px;
    margin-bottom: 5px;
  }

  .card:last-child{
    margin-right: 0px;
  }

  .col-md-2{
    max-width: 15.666667%!important;
  }

  .product-container{
    margin-left: 15px;
  }

</style>

