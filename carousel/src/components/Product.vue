<template>
    <li class="product" ref="product">
        <img :src="image" :alt="alt" class="product__image">
        <span class="product__name">{{name}}</span>
        <span class="product__price" v-if="currency == 'GBP'">£{{price}}</span>
        <span class="product__price" v-else>{{currency}}{{price}}</span>
        <a :href="url" class="product__action" target="_blank">View Product</a>
    </li>
</template>

<script>
export default {
    name: 'product',
    props: {
        name: String,
        currency: String,
        price: String,
        image: String,
        url: String,
        alt: String
    }
}
</script>

<style lang="scss">

/* Product wrapper */
.products{
    display: flex;
    flex-wrap: nowrap;
    width: 100%;
}

/* Products*/
.product{
    display: inline-block;
    padding: 10px;
    min-width: (100% / 3);
    > * {
        display: block;
    }
    img{
        margin: auto;
    }
}
</style>