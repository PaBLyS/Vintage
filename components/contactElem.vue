<template>
  <div class="contactElem">
    <p class="contactElem-label">{{label}}</p>
    <a :href="url" class="contactElem-link">{{link}}</a>
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
  .contactElem {

    &-label {
      font-size: 15px;
      color: #333333;
      margin-bottom: 0;
    }

    &-link {
      font-family: SuisseIntl-SemiBold, sans-serif;
      font-size: 14px;
      color: #3db565;
      text-transform: uppercase;
    }
  }
</style>
