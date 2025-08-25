<template>
  <div id="product" class="container-fluid row">
    <!-- Add your code here -->


    <div class="row col-12 col-md-7 row-cols-2">


      <img v-for="(image_data, index) in product.media_gallery" :key="index" class="mb-4 img-fluid"
        :src="image_data.image" :alt="image_data.alt" />


    </div>
    <div class="col-12 col-md-5">
      <div class="border-bottom">
        <p class="text-left"> {{ product.product_offer_label }} </p>

        <h4 class="text-left">{{ product.product_title }}</h4>
      </div>
      <div class="row border-bottom">
        <div class="col-6 col-md-4">
          <span>Original</span>
          <p>£{{ product.rrp.toFixed(2) }}</p>
        </div>
        <div class="col-6 col-md-4">

          <span>Now</span>
          <p>£{{ product.selling_price.toFixed(2) }}</p>

        </div>
        <div class="col-6 col-md-4">50% discount</div>
      </div>

      <div class="row border-bottom">
        <img v-for="(image_data, index) in product.alternative_colours" :key="index" style="max-width:20%"
          :src="image_data.image" :alt="image_data.alt_text" />

        <!-- <img v-for="(image_data, index) in product.alternative_colours" :key="index" class="h-30 w-auto"
          :src="image_data.image" :alt="image_data.alt_text" /> -->
      </div>

      <div class="col-12 border-bottom">
        <p>Select Size</p>

        <button v-for="(size, index) in product.product_size_labels" :key="index" class="btn btn-outline-dark"> {{ size
        }}
        </button>

      </div>
      <div class="row">

        <button class="btn btn-dark btn-lg rounded-pill">Add To Bag</button>
      </div>
      <div>
        <p>Description</p>

        <p>{{ product.product_description }}</p>
        <div v-html="product.product_bulletpoints"></div>
        <p>Product Code: {{ product.product_sku }}</p>

      </div>

    </div>


  </div>

</template>

<script>
import product from './data/product.json'

export default {
  name: 'ProductPage',
  data() {
    return {
      product: product,
      // Add any other data properties you need
    }
  },
  // Any Vue lifecycle hooks and custom JavaScript code can be added here
}
</script>

<style scoped lang="scss"></style>
<!-- // Styling to be added here if needed. SASS is allowed if preferred</style> -->
