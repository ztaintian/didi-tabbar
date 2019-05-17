<template>
  <div class="home">
    <v-tabbar></v-tabbar>
  </div>
</template>

<script>
// @ is an alias to /src
import TabBar from '@/components/TabBar.vue'

export default {
  name: 'home',
  components: {
    'v-tabbar': TabBar
  }
}
</script>
