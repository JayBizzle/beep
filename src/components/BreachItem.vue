<template>
  <ion-item @click="viewBreach">
    <ion-avatar slot="start">
      <div class="img-holder">
        <img :src="breach.LogoPath" :alt="breach.Title"/>
      </div>
      <div class="avatar-shadow"/>
    </ion-avatar>
    <ion-label>
      <h1>
        {{ breach.Title }}
        <img v-show="breach.IsVerified" src="../images/Icon-Verified-Checkmark.svg" alt="Verified breach"/>
      </h1>
      <p v-html="this.$breachesService.formatDate(breach.BreachDate)"/>
      <h2 v-html="this.$breachesService.formatDomain(breach.Domain)"/>
    </ion-label>
    <ion-icon
      slot="end"
      name="arrow-forward"/>
  </ion-item>
</template>

<script>
export default {
  name: 'BreachItem',
  props: {
    breach: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    viewBreach() {
      this.$router.push('/breaches/' + this.breach.Name)
    },
  },
}
</script>

<style scoped>
ion-item {
  --padding-start: 0;
  --ion-color-shade: rgba(0, 0, 0, 0.15);
  --inner-border-width: 0;
  --border-width: 0 0 0.55px 0;
}

ion-avatar {
  position: relative;
  height: 80px;
  width: 80px;
  margin: 20px;
  border-radius: 5px;
  background-color: #f7f7f7;
  display: table;
}

.avatar-shadow {
  position: absolute;
  height: 70%;
  width: 70%;
  z-index: -1;
  top: 35%;
  left: 15%;
  border-radius: 5px;
  background-color: rgba(0, 0, 0, 0.2);
  -webkit-filter: blur(5px);
  -moz-filter: blur(5px);
  -o-filter: blur(5px);
  -ms-filter: blur(5px);
  filter: blur(5px);
}

ion-avatar .img-holder {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
}

ion-avatar .img-holder img {
  max-width: 70%;
  min-width: 1px;
  max-height: 70%;
  -o-object-fit: contain;
  object-fit: contain;
  border-radius: 0;
  overflow: visible;
}

h1 {
  height: 22px;
  color: var(--beep-light-dark);
  font-size: 18px;
  font-weight: bold;
  letter-spacing: -0.43px;
  line-height: 22px;
}

h1 img {
  margin-left: 5px;
  margin-bottom: -3px;
  width: 1.25rem;
}

p {
  height: 15px;
  color: var(--ion-dark-transparent);
  font-size: 12px;
  letter-spacing: -0.29px;
  line-height: 15px;
  margin-bottom: 10px;
}

h2 {
  height: 26px;
  color: var(--beep-light-dark);
  font-size: 14px;
  letter-spacing: -0.34px;
  line-height: 26px;
}

ion-icon {
  --ion-color-base: #c7c7cc;
}
</style>
