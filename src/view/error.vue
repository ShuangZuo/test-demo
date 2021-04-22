<template>
  <div class="error">
    <p>用户名或密码错误！</p>
  </div>
</template>

<script>
export default {
  name: 'Error',
  data () {
    return {}
  },
  created () {},
  methods: {}
}
</script>

<style scoped>
.error {
  margin-top: 10%;
  font-size: 22px;
  text-align: center;
  color: red;
}
</style>
