<template>
  <section>
    <first-block />
    <second-block />
    <third-block />
  </section>
</template>

<script>
  import firstBlock from '../components/block/firstBlock'
  import secondBlock from "../components/block/secondBlock"
  import thirdBlock from "../components/block/thirdBlock";

  export default {
    components: {firstBlock, secondBlock, thirdBlock}
  }
</script>

<style>

</style>
