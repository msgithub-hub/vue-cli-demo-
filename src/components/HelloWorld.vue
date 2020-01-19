<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <van-button type="danger">危险按钮</van-button>
        <van-list
                v-model="loading"
                :finished="finished"
                finished-text="没有更多了"
                @load="onLoad"
        >
            <van-cell
                    v-for="item in list"
                    :key="item"
                    :title="item"
            />
        </van-list>
    </div>
</template>

<script>
    // import {Button as vButton,List} from 'vant'

    export default {
        name: "",
        // components:{
        //     vButton,List
        // },
        data() {
            return {
                msg: 'haha',
                list:[],
                loading: false,
                finished: false
            }
        },
        methods:{
            onLoad(){
                // 异步更新数据
                // setTimeout(() => {
                    for (let i = 0; i < 10; i++) {
                        this.list.push(this.list.length + 1);
                    }
                    // 加载状态结束
                    this.loading = false;

                    // 数据全部加载完成
                    if (this.list.length >= 30) {
                        this.finished = true;
                    }
                // }, 500);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
