<template>
  <div class="login">
    <header class="header cf">
      <a 
        class="site-logo" 
        href="http://www.meituan.com">美团网</a>
    </header>
    <div class="promotion-banner">
      <img 
        src="//s0.meituan.net/bs/file/?f=fe-sso-fs:build/page/static/banner/www.jpg" 
        width="480" 
        height="370" 
        alt="美团网">
    </div>
    <div class="login-section">
      <h4 
        v-if="error" 
        class="tips">
        <i />
        {{ error }}
      </h4>
      <span class="login-type">账号登录
      </span>
      <i class="icon icon-user"/>
      <el-input 
        v-model="username" 
        prefix-icon="profile" 
        class="f-text "/>
      <el-input 
        v-model="password" 
        prefix-icon="password" 
        type="password" 
        class="f-text "/>
      <div class="foot">
        <el-checkbox v-model="checked">7天内自动登录</el-checkbox>
        <b>忘记密码?</b>
      </div>
      <el-button 
        type="success" 
        size="mini" 
        class="btn" 
        @click="login">登录</el-button>
      <div />
    </div>
    <footer class="footer">
      <div class="site-info-nav cf">
        <ul>
          <li class="first"><a 
            rel="nofollow" 
            href="https://about.meituan.com/about.html">关于美团</a></li>
          <li><a 
            rel="nofollow" 
            href="https://zhaopin.meituan.com/">加入我们</a></li>
          <li><a 
            rel="nofollow" 
            href="http://emis.meishi.meituan.com/merchantsSettled">商家入驻</a></li>
          <li><a 
            rel="nofollow" 
            href="https://www.meituan.com/help/faq">帮助中心</a></li>
          <li class="last"><a href="http://meituan.com/mobile">美团手机版</a></li>
        </ul>
      </div>
      <div class="copyright">
        <p>
          ©<span>2018</span>
          <a href="https://www.meituan.com/">美团网团购</a>
          meituan.com
          <a 
            href="http://www.miibeian.gov.cn/" 
            target="_blank">京ICP证070791号</a>
          京公网安备11010502025545号
        </p>
      </div>
    </footer>
  </div>
</template>

<script>
  import CryptoJS from 'crypto-js'
  export default {
    layout: "blank",
    data() {
      return {
        checked: '',
        username: '',
        password: '',
        error: ''
      }
    },
    methods: {
      login() {
        let self = this;
        self.axios.post('/users/signup', {
          username: window.encodeURIComponten(self.ruleForm.name),
          password: CryptoJS.MD5(self.ruleForm.pwd).toString(),
        }).then((status, data) => {
          if (status.code === 200) {
            if (data && data.code === 0) {
              location.href = '/'
            } else {
              self.error = data.msg
            }
          } else {
            self.error = `服务器出错,错误码:${status}`
          }
          setTimeout(function () {
            self.error = ''
          }, 1500)
        })
      }
    }
  }

</script>
<style lang="scss">
   @import "../assets/css/login/index.scss";
</style>
