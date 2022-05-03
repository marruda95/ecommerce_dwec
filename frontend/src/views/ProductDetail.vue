<template>
  <div class="container">
        <section class="py-5">
            <div class="container px-4 px-lg-5 my-5">
                <div class="row gx-4 gx-lg-5 align-items-center">
                    <div class="col-md-6"><img class="card-img-top mb-5 mb-md-0" :src="product.mainImage" :alt="product.name" /></div>
                    <div class="col-md-6">
                        <h1 class="display-5 fw-bolder">{{product.name}}</h1>
                        <div class="fs-5 mb-5">
                            <span>$ {{product.price}}</span>
                        </div>
                        <p class="lead">{{product.short}}</p>
                        <input class="form-control text-center me-3" id="inputQuantity" type="num" value="1" style="max-width: 3rem" /><br>
                        <div class="d-flex">
                            <button class="btn btn-outline-dark flex-shrink-0" type="button">
                                <i class="bi-cart-fill me-1"></i>
                                Add to cart
                            </button>
                            <button class="btn btn-outline-dark flex-shrink-0" type="button">
                                <i class="bi-cart-fill me-1"></i>
                                Add to Wishlist
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Related items section-->
        <section class="py-5 bg-light">
            <div class="container px-4 px-lg-5 mt-5">
                <h2 class="fw-bolder mb-4">Others Also Bought</h2>
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                    <div class="col mb-5">
                        <div class="card h-100">
                            <img class="card-img-top" :src="product.mainImage" :alt="product.name" />
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <h5 class="fw-bolder" >{{product.name}}</h5>
                                    $ {{product.price}}
                                </div>
                            </div>
                            <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                                <div class="text-center"><b-button variant="primary" :to="'/product/'+product.id">Ver</b-button></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
  </div>
</template>

<script>
import url from '../utils/api'
export default {
  name: 'Product',
  components: {
  },
  data(){
    return {
      product: {}
    }
  },
  computed: {
   
  },
  created() {
    fetch(url(`/products/${this.$route.params.id}`))
      .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.product = data
        } )
  }
}

</script>



