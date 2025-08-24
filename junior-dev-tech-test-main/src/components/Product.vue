<template>
  <div id="product">
    <!-- Add your code here -->

    <div id="parent">
      <div id="left-container">
        <img v-for="(image_data, index) in product.media_gallery" :key="index" class="image-container "
          :src="image_data.image" :alt="image_data.alt" />
      </div>
      <div id="right-container">
        <p class="text-center">{{ product.product_title }}</p>
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

<style scoped lang="scss">
#parent {
  display: flex;
  margin-left: 2.5%;
  margin-right: 2.5%;
}

#left-container {
  display: flex;
  flex-basis: 60%; // Fixed 60% width
  flex-flow: row wrap;

}

#right-container {
  display: flex;
  flex-basis: 40%;
  flex-direction: column;
}

.image-container {
  // flex-basis: 50%; // Each image takes 50% of container width minus padding, making them appear side-by-side
  padding: 5px; // between each image

}

img {
  max-width: 50%;
  max-height: 50%; // Fill the container width

}
</style>
<!-- // Styling to be added here if needed. SASS is allowed if preferred</style> -->
