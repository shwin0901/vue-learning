<template>
    <div>

        <form v-if="!isRad" class="login">
            <h3>欢迎登录</h3>
            <div class="log">
                <div class="username">
                    <label> 用户名</label>
                    <input type="text" v-model="name">
                </div>
                <div class="password">
                    <label>密码</label>
                    <input type="password" v-model="password">
                </div>
            </div>
            <div class="btn">
                <button type="button" class="loginBtn" @click="login()">登录</button>
                <button type="button" @click="reg()">注册</button>
            </div>
        </form>
        <form v-else class="loginList">
            <h3>请输入以下信息</h3>
            <div class="inputList">
                <div>
                    <label>用户名</label>
                    <input type="text" v-model="name">
                </div>
                <div class="password2">
                    <label>密码</label>
                    <input type="text" v-model="password">
                </div>
                <div>
                    <label>再次密码</label>
                    <input type="text" v-model="repeat">
                </div>
            </div>
            <div class="btn2">
            <button type="button" class="loginBtn" @click="addUser()">确定</button>
            <button type="button" @click="cancel()">取消</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: "login",
        data() {
            return {
                isRad: false,
                name: '',
                password: '',
                repeat: ''
            }
        },
        methods: {
            login() {
                if (localStorage.getItem("name") === this.name && localStorage.getItem("password") === this.password) {
                    this.name = '';
                    this.password = '';
                    this.$router.replace("/home/list");
                } else {
                    alert("用户名或密码不正确！")
                }
            },
            reg() {
                this.isRad = true;
                this.name = '';
                this.password = ''
            },
            cancel() {
                this.isRad = false
            },
            addUser() {
                if (this.name !== '' && this.password !== '') {
                    if (this.password === this.repeat) {
                        localStorage.setItem('name', this.name);
                        localStorage.setItem('password', this.password);
                        this.name = '';
                        this.password = '';
                        this.repeat = '';
                        this.isRad = false
                    } else {
                        alert('两次输入密码不一样！')
                    }
                } else {
                    alert("请输入用户名或密码！");
                }

            }
        }
    }
</script>

<style scoped lang="scss">
    h3 {
        margin: 50px 0 0 50px;
    }
    .log {
        display: flex;
        justify-content: flex-end;
        flex-wrap: wrap;
        margin: 0 60px 0 20px;
    }

    .username {
        margin: 26px 0 10px 0;
    }

    .password {
        margin: 0 0 40px 0;
    }

    .btn {
        display: flex;
        justify-content: space-around;
        margin: 0 30px;
    }

    input {
        height: 28px;
        width: 240px;
        font-size: 14px;
        border-radius: 4px;
        border: 1px solid #d8d8d8;
    }

    label {
        margin: 0 10px 0 0;
    }

    button {
        width: 46%;
        height: 38px;
        border-radius: 6px;
        color: #42b983;
        font-size: 16px;
    }

    .inputList {
        display: flex;
        justify-content: flex-end;
        flex-wrap: wrap;
        margin: 26px 60px 40px 20px;
    }
    .btn2 {
        display: flex;
        justify-content: space-around;
        margin: 0 30px;
    }
    .password2 {
        margin: 10px 0;
    }
    .loginBtn {
        background-color: #42b983;
        color: white;
        border-color: #42b983;
    }
</style>