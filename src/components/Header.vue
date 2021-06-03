<template>
  <div class="return-home navigation" @click="routeToHome">
    <span class="material-icons-outlined d-block" style="margin-bottom: -10px"
      >home</span
    >
    <span>Home</span>
  </div>
  <h1 class="mt-5 m-sm-5 mb-0 display-3" style="color: white">{{ title }}</h1>
  <hr class="d-sm-block d-none" />
</template>

<script>
export default {
  name: 'Header',
  props: ['title'],
  methods: {
    routeToHome() {
      this.$router.push({ name: 'Home' })
    }
  }
}
</script>

<style></style>
