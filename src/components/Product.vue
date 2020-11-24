<template>
  <div class="product-gallery">
    <div class="gallery">
      <div
        class="gallery-item-wrapper"
        v-for="(item, index) in images"
        :key="'img' + index"
        @click="activeImg = index"
      >
        <div
          class="gallery-item"
          :style="{
            'background-image': 'url(' + require('../assets/' + item) + ')',
          }"
        ></div>
      </div>
    </div>   
    <v-card>
      <v-img
        :src="imageUrl"
        contain
        max-width="500"
        alt="../assets/logo.png"
      ></v-img>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ["images"],
  data: () => {
    return { activeImg: 0 };
  },
  computed: {
    // Função utilizada para computar dinamicamente o caminho para a imagem
    imageUrl() {
      var imagem = require.context("../assets/", false, /\.png$/);
      return imagem("./" + this.images[this.activeImg]);    
    },
  },
};
</script>

<style lang="scss" scoped>
@mixin bg-image() {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.product-gallery {
  display: flex;

  .gallery {
    width: 20vh;  
    padding: 0 16px 100px; 

    .gallery-item-wrapper {
      border: 1px solid black;
      height: calc(10vh - 5px);
      margin-top: 5px;

      .gallery-item {
        width: 100%;
        height:  100%;
        cursor: pointer;
        @include bg-image;
      }
    }
  }
}
</style>