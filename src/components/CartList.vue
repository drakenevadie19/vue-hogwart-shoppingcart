<template>
    <div>
        <div v-for="item in list" :key="item.id">
            <CartListItem
                :item="item"
                @cart-del = "$emit('cart-del', $event)"
                @cart-update-num = "$emit('cart-update-num', $event)"
            ></CartListItem>
        </div>
    </div>
</template>

<script>
    import CartListItem from './CartListItem.vue';
    export default {
        props: ['list'],
        emits: ['cart-del', 'cart-update-num'],
        components: {
            CartListItem,
        },
    };
</script>

<style scoped></style>