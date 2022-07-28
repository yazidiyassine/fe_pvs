<template>
  <v-app id="bg">
    <router-view />
  </v-app>
</template>

<script>
export default {
  name: "App",
  methods: {
    changeRTL() {
      this.$vuetify.rtl = 0.0;
    },
  },
};0
</script>
<style>
@import url(https://fonts.googleapis.com/earlyaccess/droidarabicnaskh.css);
/* font-family: 'Droid Arabic Naskh',Arial, Helvetica,  sans-serif; */

@import url(https://fonts.googleapis.com/earlyaccess/amiri.css);

#bg {
  background: repeating-radial-gradient(
      circle,
      transparent,
      transparent 5.6px,
      #eae8e4 5.6px,
      #eae8e4 7.2px
    ),
    repeating-radial-gradient(
      circle,
      transparent,
      transparent 5.6px,
      #eae8e4 5.6px,
      #eae8e4 7.2px
    ),
    #f0f0f0;
  background-size: 32px 32px;
  background-position: 0 0, 16px 16px, 32px 16px;
  background-color: #f0f0f0;
  font-family: "Droid Arabic Naskh", Arial, Helvetica, sans-serif;

  font-size: 18px;
  line-height: 28px;
  text-decoration: none;
  color: black;
}
</style>
