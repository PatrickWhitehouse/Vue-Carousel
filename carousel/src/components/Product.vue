<template>
    <li class="product" ref="product">
        <a :href="url" target="_blank" :title="name">
            <img :src="image" :alt="alt" class="product__image">
            <span class="product__name">{{name}}</span>
            <span class="product__price" v-if="currency == 'GBP'">£{{price}}</span>
            <span class="product__price" v-else>{{currency}}{{price}}</span>
            <button class="product__action" target="_blank">View Product</button>
        </a>
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