<template>
    <div class="product">
        <img :src="image" :alt="name" class="product__image">
        <span class="product__name">{{name}}</span>
        <span class="product__price">{{currency}}{{price}}</span>
        <button class="product__action">View Product</button>
    </div>
</template>

<script>
export default {
    name: 'product',
    props: {
        name: String,
        currency: String,
        price: String,
        image: String
    }
}
</script>

<style lang="scss">

/* Product wrapper */
.products{
    display: flex;
    flex-wrap: wrap;
}

/* Products*/
.product{
    display: inline-flex;
    flex-direction: column;
    padding: 10px;
}
</style>