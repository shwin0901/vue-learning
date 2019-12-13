<template>
    <div>
<!--        <div v-if="look">-->
<!--            <div>fhajsk</div>-->
<!--            <button @click="back"> 返回</button>-->
<!--        </div>-->
        <ul v-if="look">
            <li v-for="(item,index) in list" :key="index" class="card" @click="son(index)">
                <h3 class="title">{{item.title}}</h3>
                <p class="content">{{item.content}}</p>
                <small class="time">{{item.time}}</small>
                <small v-show="shon === index" class="sen" @click="details(item)">查看详情>></small>
            </li>
            <p v-show="list.length == 0" class="none" >这里什么也没有！</p>
        </ul>
        <info  @backEvent="() => {this.look = true}" v-bind:obj="InfoData" v-else>

        </info>
    </div>
</template>

<script>
    import store from '../store/index'
    import Info from "./info";

    export default {
        name: "list",
        components: {Info},
        store,
        data() {
            return {
                look: true,
                shon:'',
                InfoData:''
            }
        },
        computed: {
            list() {
                return store.state.lists;
            },
        },
        methods:{
            details: function(item) {
                this.look = false;
                this.InfoData = item
            },
            son(index){
                this.shon = index
            },
        }
    }
</script>

<style scoped lang="scss">
    .none {
        text-align: center;
    }

    .card {
        margin: 16px;
        border-radius: 4px;
        list-style: none;
        box-shadow: 0.5px 0.5px 5px 2px rgba(0, 0, 0, 0.1);
        padding: 0 0 6px;
    }

    .card:hover {
        background-color: #42b983;
        color: white;
    }

    .sen {
        display: none;
        position: relative;
        left: 180px;
    }

    .card:hover .sen {
        display: inline;
    }

    .title {
        padding: 10px 4px 6px 4px;
        margin: 0 6px 0 6px;
        border-bottom: #e1e1e1 1px solid;
    }

    .content {
        padding: 6px 10px 6px 10px;
        /*color: #3e3e3e;*/
    }

    .time {
        padding: 2px 10px 6px 10px;
        /*margin: 20px;*/
        /*color: #505050;*/
        /*display: block;*/
    }
</style>