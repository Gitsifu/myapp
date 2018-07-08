<template>
  <div>
    <!--头部 start-->
    <b-container>
      <b-row>
        <b-col class="head">
          <div class="head-h">
            欢迎登陆
          </div>
          <div class="head-r">
            <img src="../assets/icon-607055_ee33a3e.gif" width="18px">
            “登录页面”意见反馈
          </div>
        </b-col>
      </b-row>
    </b-container>
    <!--头部 end-->

    <!--主体 start-->
    <div class="main">
      <div class="main-form">
        <img src="../assets/scan_ec8538d.png" class="main-img">
        <img src="../assets/scan-tip_8bee6e1.png" class="main-img-scan">
        <tabs value="name1" style="margin-top: 30px">
          <tab-pane :label="label1" name="name1">
            <i-form ref="formInline" :model="formInline" :rules="ruleInline">
              <form-item prop="user">
                <i-input type="text" v-model="formInline.user" placeholder="手机/邮箱/用户名">
                  <icon type="ios-person-outline" slot="prepend"></icon>
                </i-input>
              </form-item>
              <form-item prop="password">
                <i-input type="password" v-model="formInline.password" placeholder="密码">
                  <icon type="ios-locked-outline" slot="prepend"></icon>
                </i-input>
              </form-item>
              <div class="form-checkbox">
                <checkbox v-model="single">两周内自动登陆</checkbox>
                <span style="font-size: 12px; float: right;margin-top: 2px">忘记密码</span>
              </div>
              <form-item>
                <i-button style="background-color: #ff9000; color: #fff" @click="handleSubmit('formInline')" long large>
                  登陆
                </i-button>
              </form-item>
            </i-form>

          </tab-pane>
          <tab-pane :label="label2" name="name2">手机动态登陆</tab-pane>
        </tabs>
        <div class="form-footer">
          <div style="color: #999">使用第三方账号登陆</div>
          <br/>
          <span style="float: right;color:#f60;">注册新账号></span>
        </div>
      </div>
    </div>
    <!--主体 eng-->

    <!--底部 start-->
    <div class="footer" style="padding-top: 46px;">
      <div style="text-align: center;color: #666;font-size: 12px;line-height: 30px;">
        <span>关于我们</span>
        <span class="footer-partition">|</span>
        <span>联系方式</span>
        <span class="footer-partition">|</span>
        <span>广告服务</span>
        <span class="footer-partition">|</span>
        <span>新闻中心</span>
        <span class="footer-partition">|</span>
        <span>网站地图</span>
        <span class="footer-partition">|</span>
        <span>公司资质</span>
        <span class="footer-partition">|</span>
        <span>加入我们</span>
        <span class="footer-partition">|</span>
        <span>支付方式</span>
        <span class="footer-partition">|</span>
        <span> 我也要与EASY SIGNING合作</span>
        <span class="footer-partition">|</span>
        <span> 热门服务</span>
        <span class="footer-partition">|</span>
        <span> EASY SIGNING移动版</span>
      </div>
      <div style="text-align: center; font-size: 12px; color: #999;margin-bottom: 10px;">
        Copyright 2005-2018zbj.com 版权所有渝ICP备10202274-1号渝B2-20080005
      </div>

      <div style="text-align: center;">
        <img src="../assets/ebs_f4a49dc.png" class="footer-img"/>
        <img src="../assets/xfz_ad6bc96.jpg" class="footer-img"/>
        <img src="../assets/time_cnnic_f555083.jpg" class="footer-img"/>
        <img src="../assets/chengxin_c4e50cf.png" class="footer-img"/>
      </div>
    </div>
    <!--底部 end-->
  </div>

</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        single: false,
        formInline: {
          user: '',
          password: ''
        },
        ruleInline: {
          user: [
            {required: true, message: 'Please fill in the user name', trigger: 'blur'}
          ],
          password: [
            {required: true, message: 'Please fill in the password.', trigger: 'blur'},
            {type: 'string', min: 6, message: 'The password length cannot be less than 6 bits', trigger: 'blur'}
          ]
        },
        label1: (h) => {
          return h('div', {
              style: {
                'font-size': '16px',
              }
            },
            '账号密码登陆'
          )
        },
        label2: (h) => {
          return h('div', {
              style: {
                'font-size': '16px',
              }
            },
            '手机动态登陆'
          )
        }
      }

    },
    methods: {
      handleSubmit(name) {
        this.$refs[name].validate((valid) => {
          if (valid) {
            this.$Message.success('Success!');
          } else {
            this.$Message.error('Fail!');
          }
        })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .head {
    height: 115px;
    line-height: 115px;
  }

  .head-h {
    display: inline-block;
    padding-left: 25px;
    line-height: 64px;
    border-left: 1px solid #888;
    font-size: 26px;
    color: #888;
  }

  .head-r {
    font-size: 12px;
    margin-top: 75px;
    float: right;
    padding-right: 85px;
    line-height: 40px;
    color: #ff9400;
  }

  .main {
    background-image: url('../assets/bgimg.jpg');
    min-width: 324px;
    background-size: cover;
    background-position: center;
    position: relative;
    background-repeat: no-repeat;
    height: 550px;
    width: 100%;
  }

  .main-form {
    position: absolute;
    width: 330px;
    height: 419px;
    margin-top: 40px;
    right: 190px;
    background-color: #fff;
    border: 1px solid #e5e5e5;
    padding: 10px 20px;
  }

  .main-img {
    position: absolute;
    top: 5px;
    right: 5px;
  }

  .main-img-scan {
    position: absolute;
    top: 5px;
    right: 60px;
  }

  .form-checkbox {
    margin: 20px 0;
  }

  .form-footer {
    height: 86px;
    width: 100%;
    position: absolute;
    bottom: 0;
    left: 0;
    background-color: #f3f3f3;
    font-size: 12px;
    padding: 20px;

  }

  .footer-partition {
    padding: 0 5px;
  }

  .footer-img {
    margin: 0 10px;
  }

  @media only screen and (max-width: 768px) {
    .main {
      background-image: none;

    }

    .main-form {
      position:relative;
      margin: auto;
      margin-top: 30px;
      right: 0;
    }
    .footer {
      display: none;
    }

  }
</style>
