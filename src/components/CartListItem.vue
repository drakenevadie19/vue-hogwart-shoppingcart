<template>
    <div class="item">
        <img :src="item.img" />
        <div class="name">{{ item.name }}</div>
        <div class="change">
            <!--Subtract 1 item-->
            <a href="" v-if="item.num >0" @click.prevent="subtractOne(item.id, item.num)" >
                <el-icon><Minus /></el-icon>
            </a>
            
            <a href="" v-else style="pointer-events: none;">
                <el-icon><Minus /></el-icon>
            </a>
            <!--Inform number-->
            <input 
                type="text" 
                class="num"
                :value="item.num"
                @blur ="changeNum(item.id, $event)"
            >
            <!--Plus 1 item to cart-->
            <a href="" @click.prevent="addOne(item.id, item.num)">
                <el-icon><Plus /></el-icon>
            </a>
        </div>
        <div class="del" @click.prevent="del(item.id)">
            <el-icon><Delete /></el-icon>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['item'],
        emits: ['cart-del', 'cart-update-num'],
        methods: {
            del: function(id) {
                 //However, delete should really occur in parent
                 //since the list in this component is just a copy from parenty 
                 //so this component should let parent component, my-cart delete one product from list
                 this.$emit('cart-del', id);
            }, 
            changeNum: function(id, event) {
                //Pass id and new num to parent component
                this.$emit('cart-update-num', {
                    id: id,
                    num: event.target.value,
                });
            },
            subtractOne: function(id, currentNum) {
                console.log(typeof currentNum);
                this.$emit('cart-update-num', {
                    id: id,
                    num: currentNum - 1,
                });
            },
            addOne: function(id, currentNum) {
                console.log(typeof currentNum);
                this.$emit('cart-update-num', {
                    id: id,
                    num: currentNum + 1,
                });
            },
        },
    };
</script>

<style lang="scss" scoped> 
    .item {
        height: 55px;
        line-height: 55px;
        position: relative;
        border-top: 1px solid purple;
        img {
            max-width: 40px;
            margin: 5px;
        }
        .name {
            position: absolute;
            width: 200px;
            top: 0;
            left: 55px;
            font-size: 16px;
        }
        .change {
            width: 100px;
            position: absolute;
            top: 0;
            right: 50px;
            a {
                font-size: 20px;
                width: 40px;
                height: 25px;
                text-decoration: none;
                background-color: lightgray;
                vertical-align: middle;
                text-align: center;
            }
            .num {
                width: 40px;
                height: 20px;
            }
        }
        .del {
            position: absolute;
            top: 0;
            right: 0px;
            width: 40px;
            text-align: center;
            font-size: 40px;
            cursor: pointer;
            &:hover {
                background-color: red;
            }
        }
    }
</style>