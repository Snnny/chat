<template>
  <div class="login">
    <div class="bg"></div>
    <h1>登录</h1>

    <!-- 头像 -->
    <div class="avatar-wrapper">
      <div class="avatar">
        <img src="../assets/images/chat.jpg" alt="avatar">
      </div>
    </div>
    <!-- 用户名&密码 -->
    <div class="userInput">
      <div class="enter name">
        <label class="user-label">账号</label>
        <input type="text" name="" placeholder="请输入用户名" autofocus autocomplete="off">
      </div>
      <div class="enter password">
        <label class="user-label">密码</label>
        <input :type="pwdType" name="" placeholder="请输入密码">
        <span class="eye" @click="toggleSee" :class="{active: showPwd}"> 0000 </span>
      </div>
    </div>
    
    <!-- login -->
    <div class="handle">
      <mt-button type="primary" size="normal" plain>登录</mt-button>
    </div>
    

    <!-- 第三方登录 -->

    <div class="others">
      <div class="other" v-for="item of thirds"> <span>{{ item }}</span></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'login',
  data () {
    return {
      avatar: '../assets/images/chat.jpg',
      showPwd: false,
      pwdType: 'password',
      thirds: ['QQ', '微信', '微博']
    }
  },
  created () {
    this.init()
  },
  methods: {
    init () {
      console.log('11111')
    },
    toggleSee () {
      this.showPwd = !this.showPwd
      this.pwdType = this.pwdType === 'password' ? 'text' : 'password'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../common/mixins.scss';
.login {
  position: relative;
  width: 100%;
  height: 100%;
  padding-top: rem(50);
  /* 模糊背景 */
  .bg {
    position: absolute;
    z-index: -1;
    width: 100%;
    height: 100%;
    background: url('../assets/images/login-bg.jpg');
    background-size: cover;
    filter: blur(40px);
  }
  h1 {
    text-align: center;
    color: #343ccc;
    @include font-dpr(50px);
  }
  /* 头像 */
  .avatar-wrapper {
    position: relative;
    width: 100%;
    height: rem(400);
    margin: rem(60) 0;
    .avatar {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      width: rem(250);
      height: rem(250);
      border-radius: 50%;
      overflow: hidden;
      img {
        width: rem(250);
      }
    }
  }
  /* 用户名&密码 */
  .userInput {
    position: relative;
    width: 100%;
    height: rem(300);
    .enter {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      margin: rem(20) 0;
      width: rem(450);
      height: rem(90);
      border-bottom: 1px solid #fff;
      color: #fff;
      input {
        position: absolute;
        right: 0;
        height: 100%;
        outline-style: none;
        border: 0px;
        width: rem(300);
        background-color: transparent;
        @include font-dpr(32px);
        color: #fff;
        line-height: rem(90)
      }
      ::-webkit-input-placeholder {
        @include font-dpr(32px);
        color: #fff;
      }
      .user-label {
        line-height: rem(90);
        display: inline-block;
        height: 100%;
        width: rem(120);
        text-align: center;
        @include font-dpr(40px);
      }
      &.name {
        top: 0;
      }
      &.password {
        top: rem(120);
         .eye {
            position: absolute;
            right: 0;
            z-index: 2;
            width: rem(50);
            line-height: rem(100);
            margin-right: rem(10);
            &.active {
              color: #f00
            }
          }
      }
    }
  }
  /*登录按钮区域*/
  .handle {
    text-align: center;
  }
  /* 第三方 */
  .others {
    display: flex;
    margin: rem(100) auto;
    width: rem(500);
    height: rem(300);
    border-top: 1px solid #fff;
    .other {
      flex: 1;
      text-align: center;
      align-items: center
    }
  }
}

</style>
