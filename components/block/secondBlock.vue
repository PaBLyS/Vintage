<template>
  <div class="secondBlock">
    <b-container>
      <b-row>
        <b-col>
          <h2 class="secondBlock-label">Our Offices</h2>
          <ul class="secondBlock-list">
            <li v-for="(elem, index) in offices" @click="editActive(index)" :class="{'secondBlock-list__elem': true, active: index === active}">
              {{elem.city}}
            </li>
          </ul>
          <h2 class="secondBlock-sublabel">Global Message Services Ukraine LLC</h2>
          <div>
            <p class="secondBlock-address">
              {{offices[active].address}}<br>
              {{offices[active].index}}<br>
              {{offices[active].country}}
            </p>
          </div>
        </b-col>
        <b-col>
          <map-block :point="offices[active]"/>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
    import mapBlock from "../mapBlock";

    export default {
        name: "secondBlock",
        components: {mapBlock},
        data() {
            return {
                active: 0,
                offices: [
                    {
                        city: 'Kyiv',
                        address: 'Kuiv, Stepan Bandera, 33 02066',
                        index: '02066',
                        country: 'Ukraine',
                        point: {
                            lat: 123,
                            lng: 234
                        }
                    },
                    {
                        city: 'New york',
                        address: 'New York, Stepan Bandera, 33 02066',
                        index: '02068',
                        country: 'USA',
                        point: {
                            lat: 123,
                            lng: 234
                        }
                    },
                    {
                        city: 'Guangzhou',
                        address: 'Guangzhou, Stepan Bandera, 33 02066',
                        index: '02063',
                        country: 'China',
                        point: {
                            lat: 123,
                            lng: 234
                        }
                    },
                    {
                        city: 'barcelona',
                        address: 'Barcelona, Stepan Bandera, 33 02066',
                        index: '02076',
                        country: 'Spain',
                        point: {
                            lat: 123,
                            lng: 234
                        }
                    }
                ]
            }
        },
        methods: {
            editActive(index) {
                this.active = index
            }
        }
    }
</script>

<style lang="scss" scoped>
  .secondBlock {

    &-label {

    }

    &-sublabel {

    }

    &-address {

    }

    &-list {

      &__elem {

        &.active {
          color: green;
        }
      }
    }
  }
</style>
