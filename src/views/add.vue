<template>
    <div class="add-from">
        <div class="title">
            <div>标题</div>
            <input type="text" v-model="title" class="from-title">
        </div>
        <div class="content">
            <div>内容</div>
            <textarea type="text" v-model="content" rows="20" class="from-content" ></textarea>
        </div>
        <div class="btn">
            <button @click="add" class="addBtn" >添加</button>
            <button @click="cancel()" class="cancel" >取消</button>
        </div>
    </div>
</template>

<script>
    import store from '../store'

    export default {
        name: "add",
        store,
        data() {
            return {
                title: '',
                content: ''
            }
        },
        methods: {
            add() {
                store.commit('addItem', {
                    title: this.title,
                    content: this.content,
                    time: new Date()
                });
                this.title = '';
                this.content = '';
                this.$router.push("/home/list")
            },
            cancel() {
                this.$router.push("/home/user")
            }
        }
    }
</script>

<style scoped lang="scss">
    .add-from {
        margin: 16px;
    }

    p {
        margin: 4px 0;
    }

    .title {
        margin-bottom: 10px;
    }

    .from-title {
        height: 28px;
        width: 100%;
        font-size: 14px;
        border-radius: 4px;
        border: 1px solid #d8d8d8;
    }
    .from-content {
        border-radius: 4px;
        border: 1px solid #d8d8d8;
        width: 100%;
    }
    .btn{
        margin-top: 50px;
        display: flex;
        justify-content: space-around;
    }
    .addBtn {
        width: 46%;
        height: 38px;
        background-color: #42b983;
        color: white;
        border-radius: 4px;
        border-color: #42b983;
    }
    .cancel {
        width: 46%;
        height: 38px;
        color: #42b983;
        border-radius: 4px;
        border-color: #42b983;
        background-color: white;
    }
</style>