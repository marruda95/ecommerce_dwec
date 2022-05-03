<template>
  <div class="card h-100">
        <img class="card-img-top" :src="product.mainImage" :alt="product.name" />
        <div class="card-body p-4">
            <div class="text-center">
                <h5 class="fw-bolder">{{product.name}}</h5>
                $ {{product.price}}
            </div>
        </div>
        <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
            <div class="text-center"><b-button variant="primary" :to="'/product/'+product.id">View</b-button></div>
            <div class="text-center"><b-button variant="primary" @click="addProduct(product.id)">Add to Cart</b-button></div>
        </div>
        <b-alert variant="success" v-if="addCorrect" show> Success </b-alert>
    </div>
</template>

<script>
export default {
    props: ['product'],
    methods: {
        addProduct(){
            this.$emit('add-product', this.product)
            
        },
        addCorrect(){
            this.$emit('add-correct')
        }
    
    }
}
</script>

<style>

</style>