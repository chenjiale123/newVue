<template>
  <div class="login">
    <el-form
      ref="loginForm"
      :model="loginForm"
      :rules="loginRules"
      class="login-form"
      autocomplete="on"
      label-position="left"
    >

      <el-form-item prop="username">
        <span class="svg-container">
          <i class="fa fa-address-book-o peo" aria-hidden="true"></i>
        </span>
        <el-input ref="username" v-model="loginForm.username" placeholder="Username" />
      </el-form-item>

      <el-form-item prop="password">
        <span class="svg-container">
          <i class="fa fa-unlock-alt pad" aria-hidden="true"></i>
        </span>
        <el-input
          ref="password"
          v-model="loginForm.password"
          type="password"
          placeholder="Password"
        />
      </el-form-item>
      <el-button
        type="primary"
        style="width:100%;margin-bottom:30px;"
        @click.native.prevent="handleLogin"
      >Login</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      loginForm: {
        username: "",
        password: ""
      },
      loginRules: {
        username: [{ required: true, trigger: "blur" }],
        password: [{ required: true, trigger: "blur" }]
      }
    };
  },
  created(){
   this.list()
  },
  methods: {
    handleLogin() {
     
         this.$router.push('/index')
    },
    async  list(){
     const{ data:res}=await this.$http.get('/api/people')
     console.log(res)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" type="text/css">
.login {
  width: 100%;
  height: 100%;
  background: #999;
}
.login-form {
  position: relative;
  width: 520px;
  max-width: 100%;
  padding: 160px 35px 0;
  margin: 0 auto;
  overflow: hidden;
}
.el-form-item {
  position: relative;
}
.svg-container {
  position: absolute;
  // top: 3px;
  left: 10px;
  top: 2px;
  z-index: 99999;
  .pad {
    font-size: 20px;
    color: #fff;
  }
  .peo {
    font-size: 20px;
    color: #fff;
  }
}
.el-input {
  display: inline-block;
  height: 47px;
  width: 85%;
  background: none;
    
  input {
    background: none;
  padding-left: 30px;
  color: #fff;
  }
}
</style>
