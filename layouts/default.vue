<template>
  <div class="container mx-auto p-6">
    <nav-bar />
    <nuxt />
  </div>
</template>

<script>
import NavBar from '@/components/NavBar'

export default {
  name: 'DefaultLayout',
  components: {
    NavBar
  }
}
</script>
