<template>
    <!--  <div class="home">-->
    <!--    <img alt="Vue logo" src="../assets/logo.png">-->
    <!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <!--  </div>-->
    <div>
      <router-view/>
      <ul class="footer">
        <li class="nav"><router-link :to="{name:'list'}">List</router-link></li>
        <li class="nav"><router-link :to="{name:'user'}">User</router-link></li>
      </ul>
    </div>
</template>

<script>

    export default {
        name: 'home',
        // components: {}
    }
</script>
<style scoped lang="scss">
  li{
    list-style: none;
  }
  .footer {
    position: fixed;
    width: 100%;
    height: 60px;
    line-height: 60px;
    left: 0;
    bottom: 0;
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-around;
  }
  .nav {
    font-size: 18px;
    text-align: center;
    flex: 1;
    border-top: 1px solid #42b983;
    a{
      color: #42b983;
      display: block;
      text-decoration: none;
      &.active {
        color: #ffffff;
        background-color: #42b983;
      }
    }
  }
</style>