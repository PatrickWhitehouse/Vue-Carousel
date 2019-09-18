<template>
    <div class="product">
        <img src="https://placehold.it/200" alt="Product Name" class="product__image">
        <span class="product__name">Product Name</span>
        <span class="product__price">Product Price</span>
        <button class="product__action">View Product</button>
    </div>
</template>

<script>
export default {
    name: 'product'
}
</script>

<style lang="scss" scoped>
/* Product wrapper */
.product{
    display: inline-flex;
    flex-direction: column;
}
</style>