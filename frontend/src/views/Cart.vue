<template>
    <div class="container" >
    
        <section>
            <table class="customTable">
                <thead>
                    <tr>
                        <th>Product Name</th>
                        <th>Quantity</th>
                        <th>Price</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="product in products" :key="product.id">
                        <td>{{product.name}}</td>
                        <td>1</td>
                        <td>${{product.price}}</td>
                        <td><button @click="deleteProduct(product)">Remove</button></td>
                    </tr>
                </tbody>
            </table>
        </section>
    </div>
</template>

<script>
import url from '../utils/api'
export default {
name: 'Cart',
data(){
    return {
      products: []
    }
},
created(){
    fetch(url('/cart'))
    .then(response => response.json())
      .then(data =>  {
        console.log(`data ${data}`)
        this.products = data
        } 
    )   
},
methods: {
    deleteProduct(product) {
        let data = {id: product.id}
        fetch(url(`/cart/`+product.id), {
          method: 'DELETE',
          headers: {
            'Content-type':'application/json'
          },
          body: JSON.stringify(data)
        })
      },
      reload(){
            location.reload();
        }
},

}
</script>

<style>
    table.customTable {
        width: 100%;
        background-color: #FFFFFF;
        border-collapse: collapse;
        border-width: 0px;
        border-color: #F8F8F8;
        border-style: solid;
        color: #000000;
        text-align: left;
    }

    table.customTable td, table.customTable th {
        border-width: 0px;
        border-color: #F8F8F8;
        border-style: solid;
        padding: 5px;
    }

    table.customTable thead {
        background-color: #D4D4D4;
    }
</style>