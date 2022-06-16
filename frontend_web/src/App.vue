<script>
import FooterShop from "@/components/FooterShop.vue";
export default {
  data() {},
  components: {
    FooterShop,
  },
};
</script>

<template>
  <div class="main">
    <router-view />
  </div>
  <div class="footer">
    <FooterShop></FooterShop>
  </div>
</template>

<style>
@import "./assets/css/main.css";
@import "./assets/css/font-awesome.min.css";
@import "./assets/css/themify-icons.css";
@import "./assets/css/availability-calendar.css";
@import "./assets/css/ion.rangeSlider.css";
@import "./assets/css/ion.rangeSlider.skinFlat.css";
@import "./assets/css/jquerysctipttop.css";
@import "./assets/css/linearicons.css";
@import "./assets/css/magnific-popup.css";
@import "./assets/css/nice-select.css";
@import "./assets/css/nouislider.min.css";
@import "./assets/css/owl.carousel.css";

.main {
  width: 100%;
  height: 100%;
}
</style>
