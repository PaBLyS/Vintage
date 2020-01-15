<template>
  <div class="firstBlock">
    <b-container>
      <b-row>
        <b-col>
          <h2 class="firstBlock-label">Contacts</h2>
        </b-col>
      </b-row>
      <b-row>
        <b-col cols="6">
          <div class="firstBlock-col">
            <h3 class="firstBlock-col__sublabel"><span>GMS</span> Headquarters</h3>
            <div class="firstBlock-col__info">
              <div class="firstBlock-col__info-wrap">
                <p class="firstBlock-col__adress">Global Message Services Ukraine LLC <br>Bundesstrasse 5 | 3rd Floor
                  <br>6300 Zug <br>Switzerland</p>
                <p class="firstBlock-col__phone">+41 41 544 62 00</p>
              </div>
              <div class="firstBlock-col__info-wrap">
                <div v-for="(elem, index) in contactList" :key="elem.link + '-' + index">
                  <contact-elem :label="elem.label" :link="elem.link" :url="elem.url"/>
                </div>
              </div>
            </div>
          </div>
        </b-col>
        <b-col cols="6">
          <div class="firstBlock-col">
            <h3 class="firstBlock-col__sublabel">Technical support <span>24/7</span></h3>
            <p class="firstBlock-col__content">GMS understands that it can be hard to follow all new technologies. We
              regularly provide for all our clients educational trainings to make your operator`s business earn more and
              better though our best practices.</p>
            <p class="firstBlock-col__phone">+41 41 544 62 06</p>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
    import contactElem from "../contactElem"

    export default {
        components: {contactElem},
        data() {
            return {
                contactList: [
                    {
                        label: 'Email',
                        link: 'info@gms-worldwide.com',
                        url: 'mailto:info@gms-worldwide.com'
                    },
                    {
                        label: 'Send message',
                        link: 'Viber us',
                        url: 'tel:+41 41 544 62 00'
                    },
                    {
                        label: 'Send form',
                        link: 'Contact us',
                        url: '#'
                    }
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
  .firstBlock {
    display: flex;
    font-family: SuisseIntl, sans-serif;
    color: #2e2e2e;
    padding: 52px 0;

    &-label {
      font-size: 50px;
      margin-bottom: 0;
    }

    &-col {

      &__sublabel {
        font-size: 34px;
        margin: 38px 0;

        span {
          color: #3db565;
        }
      }

      &__info {
        display: flex;

        &-wrap {
          margin-right: 30px;
          display: flex;
          flex-direction: column;
          justify-content: space-between;
        }
      }

      &__adress {
        font-size: 15px;
        color: #333333;
        margin-bottom: 0;
      }

      &__phone {
        font-size: 26px;
        color: #3db565;
        margin: 25px 0 0;
      }
    }
  }
</style>
