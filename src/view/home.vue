<template>
  <div class="home">
    <h3>欢迎{{userInfo.username}}</h3>
    <h6>您的密码为{{userInfo.password}}</h6>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      userInfo: {}
    }
  },
  created () {
    if (sessionStorage.getItem('user')) {
      this.userInfo = JSON.parse(sessionStorage.getItem('user'))
    }
  },
  methods: {}
}
</script>

<style scoped>
.home {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 32px;
}
</style>
