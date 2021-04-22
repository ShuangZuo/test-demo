<template>
  <div class="login">
    登录
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      form: {
        userName: '',
        password: '',
      }
    }
  },
  methods: {
    loginHandel() {
      console.log('登录')
    }
  }
}
</script>

<style scoped>
.login {

}
</style>
