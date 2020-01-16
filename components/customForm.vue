<template>
  <form class="form">
    <div v-for="(elem, index) in inputs" :class="{'input-wrap': true, active: focus === index, novalid: novalid(index)}">
      <label :for="`${elem.label}-${index}`" class="input-wrap__label">
        <span>{{elem.label}}</span>
        <input :type="elem.type"
               :id="`${elem.label}-${index}`"
               v-model="elem.value"
               class="input-wrap__elem"
               @focus="onFocus(index)"
               @blur="onBlur(index)">
      </label>
    </div>
    <div class="form-chbox">
      <label for="chb-data" class="form-chbox__label">
        <input type="checkbox" id="chb-data" v-model="chb">
        <span class="form-chbox__text">I agree the processing of personal data</span>
      </label>
    </div>
    <button value="Get in touch" :class="{'form-submit': true, disabled: disabledSubmit()}" @click="submit" :disabled="disabledSubmit()">
      Get in touch
    </button>
  </form>
</template>

<script>
    import is from 'is_js'
    import axios from 'axios';

    export default {
        name: "customForm",
        data() {
            return {
                focus: null,
                valid: [false, false, false],
                inputs: [
                    {
                        type: 'text',
                        label: 'Name',
                        value: '',
                        touch: true
                    },
                    {
                        type: 'text',
                        label: 'Phone',
                        value: '',
                        touch: true
                    },
                    {
                        type: 'text',
                        label: 'Email',
                        value: '',
                        touch: true
                    }
                ],
                chb: false
            }
        },
        methods: {
            disabledSubmit() {
                let res = false;
                this.valid.forEach(elem => {
                    if (!elem) res = true
                });
                return !(!res && this.chb)
            },
            onFocus(index) {
                this.focus = index
            },
            onBlur(index) {
                this.focus = null;
                this.inputs[index].touch = false
            },
            novalid(index) {
                return !this.validate(index) && !this.inputs[index].touch
            },
            validate(index) {
                let result = false;

                if (index === 0) result = /^[а-яА-ЯёЁa-zA-Z ]+$/.test(this.inputs[index].value) && this.inputs[index].value.length <= 30 && this.inputs[index].value.length > 3;
                else if (index === 1) result = /^\+380\d{9}$/.test(this.inputs[index].value);
                else if (index === 2) result = is.email(this.inputs[index].value);

                this.valid[index] = result;
                return result
            },
            async submit(e) {
                e.preventDefault();
                let obj = {
                    name: this.inputs[0].value,
                    phone: this.inputs[1].value,
                    email: this.inputs[2].value,
                    chb: false
                };
                let res = await axios({
                    method: 'post',
                    url: 'https://httpbin.org/post',
                    data: obj
                })
                console.log(res)
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

      &.novalid {
        color: #ff0000!important;
        border-bottom: 1px solid #ff0000!important;

        .input-wrap__elem {
          color: #ff0000!important;
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
