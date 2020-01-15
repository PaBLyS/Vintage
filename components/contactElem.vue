<template>
  <div class="contactElem">
    <h4 class="contactElem__label">{{label}}</h4>
    <a :href="url" class="contactElem__link">{{link}}</a>
  </div>
</template>

<script>
  export default {
    props: {
      label: String,
      link: String,
      url: String
    }
  }
</script>

<style lang="scss" scoped>

</style>