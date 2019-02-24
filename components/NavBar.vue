<template>
  <nav class="flex items-center justify-between flex-wrap mb-8">
    <nuxt-link
      class="no-underline text-green text-3xl font-black"
      to="/"
    >
      Real World Events
    </nuxt-link>
    <div>
      <nuxt-link
        class="text-green"
        to="/"
      >
        List
      </nuxt-link>
      |
      <nuxt-link
        class="text-green"
        to="/create"
      >
        Create
      </nuxt-link>
    </div>
  </nav>
</template>

<script>
export default {
  // created() {
  //   setTimeout(() => {
  //     this.show = true
  //   }, 2000)
  // }
}
</script>

<style>
</style>
