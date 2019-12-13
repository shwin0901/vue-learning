<template>
    <div class="user">
        <img src="../assets/logo.png" alt="vue">
        <p class="name">{{name}}</p>
        <p class="prese">欢迎来到用户中心！</p>
        <button @click="addTitle()" class="btn">添加</button>
    </div>
</template>

<script>
    export default {
        name: "user",
        data(){
          return{
              name:''
          }
        },
        mounted(){
            this.name = localStorage.getItem("name") ? localStorage.getItem('name') : "Vue 小伙伴"
        },
        methods:{
            addTitle() {
                this.$router.push("/add")
            }
        }
    }
</script>

<style scoped lang="scss">
    .user {
        display: flex;
        flex-direction: column;
        align-items: center;
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
    .name {
        margin: 16px 0 0;
    }
    .prese {
        margin: 8px 0 26px ;
    }
</style>