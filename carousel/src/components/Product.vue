<template>
    <div class="product">
        <img src="https://placehold.it/200" alt="Product Name" class="product__image">
        <span class="product__name">{{name}}</span>
        <span class="product__price">{{price}}</span>
        <button class="product__action">View Product</button>
    </div>
</template>

<script>
export default {
    name: 'product',
    props: {
        name: String,
        price: Number,
        url: String
    }
}
</script>

<style lang="scss" scoped>
/* Product wrapper */
.product{
    display: inline-flex;
    flex-direction: column;
}
</style>