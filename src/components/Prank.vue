<template>
  <v-container class="fill-height">
    <v-responsive class="align-center fill-height mx-auto" max-width="900">
      <marquee class="marquee">You've been pranked</marquee>
      <v-row>
        <v-col class="d-flex justify-center">
          <img class="text-center" :src="selectedImage">
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const images = ref([
      {
        image: "https://i.etsystatic.com/5175241/r/il/ed217b/996818704/il_fullxfull.996818704_3vau.jpg",
      },
      {
        image: "https://media.tenor.com/HUz1LwDn_lAAAAAM/smile.gif"
      },
    ]);

    const selectedImage = ref('');

    const selectRandomImage = () => {
      const randomIndex = Math.floor(Math.random() * images.value.length);
      selectedImage.value = images.value[randomIndex].image;
    };

    onMounted(selectRandomImage);

    return {
      selectedImage,
      selectRandomImage
    };
  },
};
</script>

<style>
.marquee {
  font-size: 100px;
  color: red;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}
</style>
