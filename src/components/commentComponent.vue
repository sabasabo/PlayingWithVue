<template>
  <div>
    <label>Anonymous: </label>
      <span>{{ text }}</span>
  </div>
</template>

<script>
export default {
  name: 'commentComponent',
  props: {
    text: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
