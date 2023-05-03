<template>
    <div class="total">
        <span>Total: {{ total }}</span>
        <el-button type="primary" round style="color: black; padding: 5px;" @click="receive">Pay Now</el-button>
    </div>
</template>

<script>
    export default{
        props: ['list'],
        methods: {
            receive: function() {
                alert(`Your total is $${this.total}. Thank you so much for shopping!!`);
            }
        },  
        computed: {
            //computed property
            total: function() {
                var t = 0;
                this.list.forEach((item) => {
                    t += item.price * item.num;
                });
                return t;
            },
        },
    };
</script>

<style lang="scss" scoped> 
    .total {
        background-color: purple;
        height: 50px;
        line-height: 50px;
        text-align: right;
        color: aliceblue;

        button {
            margin: 0 20px;
            background-color: aliceblue;
            height: 35px;
            width: 80px;
            border: 0;
            border-radius: 15px;
            font-size: large;
        }
        span {
            color: aliceblue;
            font-weight: bold;
        }
    }
</style>