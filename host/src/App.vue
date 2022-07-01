<template>
  <div>
    <label>Show UI <input type="checkbox" v-model="showUI" /></label>
    <div v-if="showUI">
      <HelloWorld msg="message" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
    HelloWorld: () => import('library1/HelloWorld'),
  },
  data() {
    return {
      message: 'Vue.js application',
      showUI: false,
    }
  },
}
</script>

<style>
.h1 {
  color: red;
}
</style>
