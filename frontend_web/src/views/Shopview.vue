<script>
import SliderShop from "@/components/SliderShop.vue";
import HeaderShop from "@/components/HeaderShop.vue";
import ProductService from "../services/Product.service";
import { mapState } from "pinia";
import { useAuthStore } from "@/stores/Auth.store";
import toastsVue from "../components/toasts.vue";
export default {
  data() {
    return {
      Products: [],
    };
  },
  components: {
    HeaderShop,
    SliderShop,
    toastsVue,
  },
  computed: {
    ...mapState(useAuthStore, {
      currentUser: "user",
    }),
  },
  methods: {
    async retrieveProduct() {
      try {
        this.Products = await ProductService.getAll();
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
    this.retrieveProduct();
  },
};
</script>
<template>
  <div class="header">
    <HeaderShop></HeaderShop>
  </div>
  <toastsVue></toastsVue>
  <div class="slider">
    <SliderShop></SliderShop>
  </div>
  <div style="margin: 20px 60px">
    <div style="text-align: center; margin: 30px 0" class="heading">
      <h2>NIKE</h2>
      <h6>Hot and available Nike products!</h6>
    </div>
    <div class="flex-row" style="margin: 0 100px">
      <div class="d-sm-flex flex-wrap justify-content-between" id="ao">
        <div class="card m-1" style="width: 18rem" v-for="item in Products" v-show="item.categories === 'nike'">
          <div class="wrapper-img d-flex align-items-center">
            <div class="image_slider">
              <div class="image_item" v-for="img in item.img">
                <img :src="img" class="card-img-top" alt="..." />
              </div>
            </div>
          </div>
          <div class="card-body product">
            <h5 class="card-title">{{ item.title }}</h5>
            <h6 class="price">{{ item.price }}$</h6>
            <router-link
              :to="{
                name: 'details',
                params: { id: item._id },
              }"
            >
              <button type="button" class="btn btn-outline-dark">View more...</button>
            </router-link>
          </div>
        </div>
      </div>
      <div style="text-align: center; margin: 100px 30px 30px 30px" class="heading">
        <h2>VANS</h2>
        <h6>Hot and available Vans products!</h6>
      </div>
      <div class="d-sm-flex flex-wrap justify-content-between" id="balo">
        <div class="card m-1" style="width: 18rem" v-for="item in Products" v-show="item.categories === 'vans'">
          <div class="wrapper-img">
            <div class="image_slider">
              <div class="image_item" v-for="img in item.img">
                <img :src="img" class="card-img-top" alt="..." />
              </div>
            </div>
          </div>
          <div class="card-body product">
            <h5 class="card-title">{{ item.title }}</h5>
            <h6 class="price">{{ item.price }}$</h6>
            <router-link
              :to="{
                name: 'details',
                params: { id: item._id },
              }"
            >
              <button type="button" class="btn btn-outline-dark" @click="nextdetailsproduct">View more...</button>
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.wrapper-img {
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.image_slider {
  display: flex;
  transition: all 0.8s ease;
}
.image_slider:hover {
  transform: translateX(-100%);
}
.image_item {
  flex: 1 0 100%;
}
</style>
