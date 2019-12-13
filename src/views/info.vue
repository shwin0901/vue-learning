<template>
    <div>
        <h3 class="title">{{obj.title}}</h3>
        <p class="content">{{obj.content}}</p>
        <button @click="back()" class="btn">返回</button>
    </div>
</template>

<script>
    export default {
        name: "info",
        props:['obj'],
        methods:{
            back() {
                this.$emit('backEvent')
            }
        }
    }
</script>

<style scoped lang="scss">
    .title {
        padding: 10px 4px 6px 4px;
        margin: 0 6px 0 6px;
        border-bottom: #e1e1e1 1px solid;
    }
    .content {
        padding: 6px 10px 26px 10px;
        /*color: #3e3e3e;*/
    }
    .btn {
        display: block;
        text-align: center;
        background-color: #42b983;
        color: white;
        width: 80%;
        height: 38px;
        border-radius: 4px;
        border-color: #42b983;
        margin: 0 auto;
    }
</style>