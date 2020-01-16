<template>
  <form class="form">
    <div v-for="(elem, index) in inputs" :class="{'input-wrap': true, active: focus === index}">
      <label :for="`${elem.label}-${index}`" class="input-wrap__label">
        <span>{{elem.label}}</span>
        <input :type="elem.type"
               :id="`${elem.label}-${index}`"
               v-model="elem.value"
               class="input-wrap__elem"
               @focus="onFocus(index)"
               @blur="onBlur()">
      </label>
    </div>
    <div class="form-chbox">
      <label for="chb-data" class="form-chbox__label">
        <input type="checkbox" id="chb-data" v-model="chb">
        <span class="form-chbox__text">I agree the processing of personal data</span>
      </label>
    </div>
    <input type="submit" value="Get in touch" class="form-submit" @click="submit">
  </form>
</template>

<script>
    export default {
        name: "customForm",
        data() {
            return {
                focus: null,
                inputs: [
                    {
                        type: 'text',
                        label: 'Name',
                        value: '',
                        validate: false,
                        touch: false
                    },
                    {
                        type: 'text',
                        label: 'Phone',
                        value: '',
                        validate: false,
                        touch: false
                    },
                    {
                        type: 'text',
                        label: 'Email',
                        value: '',
                        validate: false,
                        touch: false
                    }
                ],
                chb: false
            }
        },
        methods: {
            onFocus(index) {
                this.focus = index
            },
            onBlur() {
                this.focus = null
            },
            submit(e) {
                e.preventDefault();
                let obj = {
                    name: this.inputs[0].value,
                    phone: this.inputs[1].value,
                    email: this.inputs[2].value,
                    chb: false
                };
                console.log(obj)
            }
        }
    }
</script>

<style lang="scss" scoped>
  .form {

    &-submit {
      margin-top: 40px;
      background-color: #262626;
      font-size: 11px;
      padding: 30px 70px;
      text-transform: uppercase;
      color: #ffffff;
      border: none;
      outline: none;

      &.disabled {
        background-color: #4e4e4e;
      }

    }

    &-chbox {

      &__label {

      }

      &__text {

      }
    }
  }

  .input {

    &-wrap {
      padding: 8px 0;
      font-size: 18px;
      margin-bottom: 10px;
      border-bottom: 1px solid #000000;
      color: #000000;

      &.active {
        color: #ffffff;
        border-bottom: 1px solid #ffffff;

        .input-wrap__elem {
          color: #ffffff;
        }
      }

      &__label {
        width: 100%;

        span {
          display: inline-block;
          min-width: 60px;
        }
      }

      &__elem {
        background: none;
        outline: none;
        border: none;
        margin-left: 20px;
        width: 80%;

        &.novalid {

        }

      }
    }
  }
</style>
