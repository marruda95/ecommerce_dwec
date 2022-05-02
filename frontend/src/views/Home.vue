<template>
  <div class="home">
    <div>
      <b-jumbotron>
        <template #header>eCommi</template>
        <template #lead>
          This is a simple hero unit, a simple jumbotron-style component for calling extra attention to
          featured content or information.
        </template>

        <hr class="my-4">

          <p>
            It uses utility classes for typography and spacing to space content out within the larger
            container.
          </p>

        <b-button variant="primary" href="#">Do Something</b-button>
        <b-button variant="success" href="#">Do Something Else</b-button>
      </b-jumbotron>
      
  <section class="py-5 bg-light">
            <div class="container px-4 px-lg-5 mt-5">
                <h2 class="fw-bolder mb-4">What's New?</h2>
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center" >
                    <div class="col mb-5" v-for="product in products" :key="product.id">
                        <div class="card h-100">
                            <img class="card-img-top" :src="product.mainImage" :alt="product.name" />
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <h5 class="fw-bolder">{{product.name}}</h5>
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
    <section class="py-5 bg-light">
            <div class="container px-4 px-lg-5 mt-5">
                <h2 class="fw-bolder mb-4">Category Name </h2>
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center" >
                    <div class="col mb-5" v-for="product in products" :key="product.id">
                        <div class="card h-100">
                            <img class="card-img-top" :src="product.mainImage" :alt="product.name" />
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <h5 class="fw-bolder">{{product.name}}</h5>
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


    
    <!---  PAGINATION ---->  
    <div class="overflow-auto">
      <div class="overflow-auto">
        <b-pagination
          v-model="currentPage"
          :total-rows="rows"
          :per-page="perPage"
          aria-controls="my-table"
        ></b-pagination>

        <b-table
          id="my-table"
          :items="items"
          :per-page="perPage"
          :current-page="currentPage"
          small
        ></b-table>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

import url from '../utils/api'
export default {
  name: 'Home',
  components: {
  },
  data(){
    return {
      products: [],
      page: 0,
      perPage: 3,
      currentPage: 1,
      items: [],
    }
  },
    // para tener el nombre en la url 
  created(){
    fetch(url(`/products?_page=1&_limit=4`))
      .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.products = data
        } ),
        
        // pruebas de filtrado por categoria
    fetch(url(`/`))
      .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.product.category = data
        } )
    
  },
  computed: {
    rows(){
      return this.items.length
    }
    
  }
}
 
</script>
