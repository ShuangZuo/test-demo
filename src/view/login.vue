<template>
  <div class="login">
    <el-form
      ref="loginForm"
      :model="loginForm"
      :rules="loginRules"
      class="login-form"
      auto-complete="on"
    >
      <el-form-item label="用户名称" prop="username">
        <el-input
          v-model="loginForm.username"
          placeholder="请输入用户名称"
        >
        </el-input>
      </el-form-item>
      <el-form-item label="用户密码" prop="password">
        <el-input
          type="password"
          placeholder="请输入用户密码"
          v-model="loginForm.password">
          </el-input>
      </el-form-item>
      <el-button
        type="primary"
        plain
        size="large"
        @click.native.prevent="handleLogin"
        >登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    const validateUsername = (rule, value, callback) => {
      if (!value || /^\s+$/.test(value)) {
        callback(new Error('请填写正确用户名'))
      } else {
        callback()
      }
    }
    const validatePassword = (rule, value, callback) => {
      if (value.length < 3 || /^\s+$/.test(value)) {
        callback(new Error('请填写登录密码'))
      } else {
        callback()
      }
    }
    return {
      loginForm: {
        username: '',
        password: ''
      },
      loginRules: {
        username: [
          { required: true, trigger: 'blur', validator: validateUsername }
        ],
        password: [
          { required: true, trigger: 'blur', validator: validatePassword }
        ]
      }
    }
  },
  methods: {
    handleLogin () {
      const {username, password} = this.loginForm
      this.$refs.loginForm.validate((valid) => {
        if (!valid) return
        if (username === 'admin' && password === 'admin') {
          sessionStorage.setItem('user', JSON.stringify(this.loginForm))
          this.$router.push({
            name: 'Home'
          })
        } else {
          this.$router.push({
            name: 'Error'
          })
        }
      })
    }
  }
}
</script>

<style scoped>
.login {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.el-form-item {
  width: 87%;
}
.el-button--primary.is-plain {
  width: 50%;
}
.login-form {
  width: 500px;
  padding: 30px 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow:0px 0 26px #49c2e2;
  border-radius: 5px;
}
</style>
