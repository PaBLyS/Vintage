<template>
  <div class="thirdBlock">
    <b-container>
      <b-row>
        <b-col cols="12" lg="6">
          <h2 class="thirdBlock-label">Contact Us</h2>
          <custom-form/>
        </b-col>
        <b-col cols="12" lg="6">
          <p class="thirdBlock-content">Please tell us more about your request and give us info about your company and country</p>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
    import customForm from "../customForm";

    export default {
        name: "thirdBlock",
        components: {customForm}
    }
</script>

<style lang="scss" scoped>
  .thirdBlock {
    padding: 100px 0;
    background: url('/pattern.png');
    background-size: auto 100%;
    font-family: SuisseIntl, sans-serif;
    color: #ffffff;

    &-label {
      font-size: 34px;
      margin-bottom: 50px;
    }

    &-content {
      font-size: 18px;
      color: #000000;
      margin-top: 50px;
    }
  }
</style>
