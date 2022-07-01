<template>
  <div>
    <label>Show UI <input type="checkbox" v-model="showUI" /></label>
    <div v-if="showUI">
      <HelloWorld msg="message" />
    </div>
  </div>
</template>

<script>
import Loading from './components/Loading.vue'
import Error from './components/Error.vue'

function defineFederatedComponent(loader) {
  return () => ({
    component: loader(),
    loading: Loading,
    error: Error,
    timeout: 1000,
  })
}

export default {
  name: 'App',
  components: {
    HelloWorld: defineFederatedComponent(() => import('library1/HelloWorld')),
    // HelloWorld: () => ({
    //   component: import('library1/HelloWorld'),
    //   loading: Loading,
    //   error: Error,
    //   timeout: 1000,
    // })
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
