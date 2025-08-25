<template>
  <div id="product" class="container-fluid row">
    <!-- Add your code here -->


    <!-- <div class="row col-12 col-md-8">

      <div v-for="(image_data, index) in product.media_gallery" :key="index" class="col-6">
        <img class="img-fluid" :src="image_data.image" :alt="image_data.alt" />
      </div>

    </div> -->

    <div class="col-12 col-md-8">
      <div class="row g-2">
        <div v-for="(image_data, index) in product.media_gallery" :key="index" class="col-6">

          <img :src="image_data.image" :alt="image_data.alt" class="w-100 h-100" />

        </div>
      </div>
    </div>


    <div class="col-12 col-md-4">

      <div class="border-bottom">
        <p class="text-left header px-1 text-body-secondary"> {{ product.product_offer_label }} </p>

        <h4 class="text-left">{{ product.product_title }}</h4>
      </div>
      <div class="row border-bottom pt-2">

        <div class="col-2 col-md-3">
          <span>Original</span>
          <p><s>£{{ product.rrp.toFixed(2) }}</s></p>


        </div>
        <div class="col-2 col-md-3">

          <span>Now</span>
          <p class="text-danger">£{{ product.selling_price.toFixed(2) }}</p>
        </div>
        <div class="col-4 col-md-6 ms-auto text-danger ">| Save {{ calcDiscount(product.rrp, product.selling_price) }}%
          |
        </div>
      </div>

      <div class="row border-bottom py-2">
        <img v-for="(image_data, index) in product.alternative_colours" :key="index" style="max-width:20%"
          :src="image_data.image" :alt="image_data.alt_text" @error="$event.target.style.display = 'none'" />

        <!-- <img v-for="(image_data, index) in product.alternative_colours" :key="index" class="h-50 w-auto"
          :src="image_data.image" :alt="image_data.alt_text" /> -->
      </div>

      <div class="col-12 border-bottom py-3">
        <p class="mb-1">Select Size</p>

        <button @click="selectedSize = size" v-for="(size, index) in product.product_size_labels" :key="index"
          class="btn btn-outline-dark mx-2 "
          :class="selectedSize === size ? 'btn-dark text-light' : 'btn-outline-dark'">
          {{
            size
          }}
        </button>

      </div>
      <div class="row pt-2">

        <button @click="addToBag" class="btn btn-dark btn-lg rounded-pill button-text">Add To Bag</button>
      </div>
      <div class=" py-3">
        <h6>Description</h6>

        <p>{{ product.product_description }}</p>
        <div v-html="product.product_bulletpoints"></div>

        <p class="weight-300"> <span class="weight-500"> Product Code: </span>
          {{ product.product_sku }}</p>

      </div>
      <!-- toast-bar -->
    </div>
    <div class="toast-container position-fixed bottom-0 end-0 p-3">
      <div ref="liveToast" class="toast" role="alert" aria-live="assertive" aria-atomic="true">
        <div class="toast-header">
          <div class="rounded me-2 bg-success" style="width: 20px; height: 20px;"></div>
          <strong class="me-auto">You have selected size: {{ addedSize }}</strong>
          <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
        </div>

      </div>
    </div>
  </div>

</template>

<script>
import { Toast } from 'bootstrap';
import product from './data/product.json'

export default {
  name: 'ProductPage',
  data() {
    return {
      product: product,
      selectedSize: null,
      addedSize: null,
      toast: null,
      // Add any other data properties you need
    }
  },
  mounted() {
    this.toast = new Toast(this.$refs.liveToast, {
      autohide: true,
      delay: 2000

    })
  },
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
  methods: {
    calcDiscount(originalPrice, currentPrice) {
      const discount = 100 - (currentPrice / originalPrice * 100);
      return Math.round(discount);

    },

    addToBag() {
      if (!this.selectedSize) {
        alert('Please select your size')
      }
      if (this.selectedSize !== null) {
        this.addedSize = this.selectedSize;
        this.toast.show();
        this.selectedSize = null;

      }
    },

  }

}

</script>

<style scoped lang="scss">
.header {
  border-left: 4px solid #B32A2C;

}

.button-text {
  font-size: 18px;
  font-weight: 500;


}
</style>
<!-- // Styling to be added here if needed. SASS is allowed if preferred</style> -->
