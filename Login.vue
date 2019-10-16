<template>
  <div class="d1">
    <div>
      <mt-header title="">
        <router-link to="/" slot="left">
        <mt-button icon="back">返回</mt-button>
      </router-link>
  <mt-button icon="more" slot="right"></mt-button>
</mt-header>
    </div>
    <div>
      <img src="../assets/img/timg.jpg" >
    </div>
    <div>
      <mt-field label="手机号"   placeholder="请输入手机号" v-model="username"></mt-field>
      <mt-field label="密码" placeholder="请输入密码" type="password" v-model="password"></mt-field>
    </div>
    <div>
      <mt-button type="primary" size="large" @click.native='login'>登陆</mt-button>
      <mt-button type="primary" size="large">短信验证码登陆</mt-button>
    </div>
    <div>
      <router-link to="/">免费注册</router-link>
      <router-link to="/">忘记密码</router-link>
    </div>
  </div>
</template>
<script>
export default {
  data(){
    return{
      username:'',
      password:''
    }
  },
  methods:{
    login(){
      var phone = /^1([38]\d|5[0-35-9]|7[3678])\d{8}$/;
      var pwd =  /^[\w_-]{6,16}$/;
      if(!phone.test(this.username)){
          this.$toast({
          message: '手机号格式错误',
          position: 'center',
          duration: 1000
        });
        return;
      }
      if(!pwd.test(this.password)){
        this.$toast({
          message: '密码格式错误',
          position: 'center',
          duration: 1000
        });
        return;
      }
      this.$toast({
       message: '登陆成功',
       duration: 2000
      });
      setTimeout(()=>{
        window.location.href = 'http://www.taobao.com'; 
      },1500)
    }
  }
}
</script>
<style scoped>
  div.d1>div:nth-child(2)>img{
    width:80px;height:80px;
    border-radius: 50%;
    margin:20px 0 ;
  }
  div.d1>div:nth-child(3){
    margin-bottom: 20px;
  }
  div.d1>div:last-child{
    display: flex;
    justify-content: space-around;
  }
  div.d1>div:last-child>a{
    color:#333;
  } 
  .mint-button--primary{
    background-color: #FF5500;
    width:90%;
    margin:0 auto;
    border-radius: 80px;
    margin-bottom: 30px;
  }
  .mint-header{
    background-color:  #FF5500;
  }
</style>