<template>
  <div>
    <div>
      <h2>Contacts</h2>
      <h3><span>GMS</span> Headquarters</h3>
      <div>
        <div>
          <p>Global Message Services Ukraine LLC</p>
          <p>Bundesstrasse 5 | 3rd Floor</p>
          <p>6300 Zug</p>
          <p>Switzerland</p>
          <p>+41 41 544 62 00</p>
        </div>
        <div>
          <div v-for="(elem, index) in contactList" :key="elem.link + '-' + index">
            <contact-elem :label="elem.label" :link="elem.link" :url="elem.url"/>
          </div>
        </div>
      </div>
    </div>
    <div>
      <h3>Technical support <span>24/7</span></h3>
      <p>GMS understands that it can be hard to follow all new technologies. We regularly provide for all our clients educational trainings to make your operator`s business earn more and better though our best practices.</p>
      <p>+41 41 544 62 06</p>
    </div>
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
            url: '#'
          },
          {
            label: 'Send message',
            link: 'Viber us',
            url: '#'
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

</style>