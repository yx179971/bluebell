<template>
  <header class="header">
      <span class="logo">bluebell</span>
    <div class="search">
      <label class="s-logo"></label>
      <input type="text" class="s-input" placeholder="搜索" />
    </div>
    <div class="btns">
      <div v-show="!isLogin">
        <a class="login-btn" @click="goLogin">登录</a>
        <a class="login-btn" @click="goRegister">注册</a>
      </div>
      <div v-show="isLogin">
        <span class="user">{{ currUserName }}</span>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeadBar",
  computed: {
    isLogin() {
      return this.$store.state.isLogin;
    },
    currUserName(){
      return this.$store.state.userName;
    }
  },
  methods: {
    goLogin() {
      this.$router.push({ name: "Login" });
    },
    goRegister() {
      this.$router.push({ name: "Register" });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.header {
  width: 100%;
  height: 48px;
  position: fixed;
  background: #ffffff;
  display: flex;
  display: -webkit-flex;
  align-items: center;
  top: 0;
  z-index: 1;
  .logo {
    margin-left: 10px;
    height: 32px;
    background: url("../assets/images/logo.png") no-repeat;
    background-size: 32px 32px;
    background-position: left center;
    padding-left: 35px;
    line-height: 32px;
    flex-grow: 0;
    margin-right: 16px;
  }
  .search {
    flex-grow: 1;
    margin: 0 auto;
    max-width: 690px;
    position: relative;
    display: flex;
    display: -webkit-flex;
    .s-logo {
      width: 18px;
      height: 18px;
      background: url("../assets/images/search.png") no-repeat;
      background-size: cover;
      display: inline-block;
      position: absolute;
      top: 50%;
      margin-top: -9px;
      left: 15px;
    }
    .s-input {
      flex-grow: 1;
      -webkit-appearance: none;
      appearance: none;
      background-color: #f6f7f8;
      border-radius: 4px;
      border: 1px solid #edeff1;
      box-shadow: none;
      color: #c1c1c1;
      display: block;
      height: 36px;
      outline: none;
      padding: 0 16px 0 40px;
      width: 100%;
    }
  }
  .btns {
    flex-grow: 0;
    margin-left: 16px;
    margin-right: 10px;
    display: flex;
    display: -webkit-flex;
    align-items: center;
    .login-btn {
      border: 1px solid transparent;
      border-radius: 4px;
      box-sizing: border-box;
      text-align: center;
      letter-spacing: 1px;
      text-decoration: none;
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 0.5px;
      line-height: 24px;
      text-transform: uppercase;
      padding: 3px 16px;
      border-color: #0079d3;
      color: #0079d3;
      fill: #0079d3;
      display: inline-block;
      cursor: pointer;
      &:nth-child(1) {
        margin-right: 5px;
      }
      &:nth-child(2) {
        margin-right: 10px;
      }
    }
    .user {
      width: auto;
      height: 24px;
      background: url("../assets/images/avatar.png") no-repeat;
      background-size: 24px 24px;
      background-position: left center;
      padding-left: 28px;
      display: flex;
      display: -webkit-flex;
      align-items: center;
      &::after {
        content: "";
        width: 0;
        height: 0;
        border-top: 5px solid #878a8c;
        border-right: 5px solid transparent;
        border-bottom: 5px solid transparent;
        border-left: 5px solid transparent;
        margin-top: 5px;
        margin-left: 10px;
      }
    }
  }
}
</style>
