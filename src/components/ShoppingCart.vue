<template>
    <div class="cart">
        <CartTitle :username="username"></CartTitle>
        <CartList 
            :list="list"
            @cart-del="delCart($event)"
            @cart-update-num="updateNum($event)"
        ></CartList>
        <CartTotal :list="list"></CartTotal>
    </div>
</template>

<script>
    import CartList from './CartList.vue';
    import CartTitle from './CartTitle.vue';
    import CartTotal from './CartTotal.vue';

    export default {
        data() {
            return {
                username: 'harry',
                list: [
                    {
                        id: 1,
                        name: 'Dragon Liver',
                        price: 1500,
                        num: 1,
                        img: 'src/assets/img/DragonLiver.png'
                    },
                    {
                        id: 2,
                        name: 'Golden Snitch',
                        price: 600,
                        num: 1,
                        img: 'src/assets/img/GoldenSnitch.png'
                    },
                    {
                        id: 3,
                        name: 'Unicon Hair',
                        price: 1200,
                        num: 1,
                        img: 'src/assets/img/UnicornTailHair.png'
                    },
                    {
                        id: 4,
                        name: 'Wand',
                        price: 2000,
                        num: 1,
                        img: 'src/assets/img/Wand.jpg'
                    },
                    {
                        id: 5,
                        name: 'Nimbus 2000',
                        price: 5000,
                        num: 2,
                        img: 'src/assets/img/Nimbus2000.jpg'
                    },
                ],
            };
        },
        components: {
            CartTitle,
            CartList,
            CartTotal,
        },
        methods: {
            delCart: function(id) {
                //delete product with id from list 
                //Step 1, find index of the product to be deleted
                var index = this.list.findIndex((item) => {
                    return item.id == id;
                });
                //Step 2, delte this product
                this.list.splice(index, 1);
            },
            updateNum: function(val) {
                this.list.some((item) => {
                    if (item.id == val.id) {
                        item.num = parseInt(val.num);
                        //terminate iteration
                        return true;
                    }
                });
            },
        },
    };
</script>

<style scoped>
    .cart {
        width: 500px;
        margin: auto;
    }
</style>