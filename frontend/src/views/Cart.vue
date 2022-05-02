<template>
    <div class="container" >
        <table>
            <thead>
                <tr>
                    <th>Product</th>
                    <th>Quantity</th>
                    <th>Price</th>
                </tr>
            </thead>
            <tbody >
                <tr v-for="product in cartProducts" :key="product.id">
                    <th>{{findProductsCart.id}}</th>
                    <th>{{product.quantity}}</th>
                    <th>{{findProductsCart.price}}</th>
                    <th>{{findProductsCart.name}}</th>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import url from '../utils/api'
export default {
name: 'Cart',
data(){
    return {
      cartProducts: [],
      products: []
    }
},
created(){
    fetch(url('/cart'))
    .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.cartProducts = data
        } ),

    fetch(url('/products'))
    .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.products = data
        } )
},
computed: {
    findProductsCart(){
        return this.products.filter(product => product.id === this.cartProducts.productId)[0]
    }

}


}
</script>
