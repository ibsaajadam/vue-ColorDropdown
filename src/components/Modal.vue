<template>
  <div>
    <div v-if="show">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      show: {
        type: Boolean,
        required: true
      }
    }
  }
</script>

<style scoped>

</style>