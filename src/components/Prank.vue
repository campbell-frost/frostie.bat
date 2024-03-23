<template>
  <v-row>
    <v-col-md-3 class="frostie">
      <h1 class="blink_text">FROSTIE.BAT</h1>
    </v-col-md-3>
    <v-col-md-6>
      <marquee scrollamount="100" class="marquee">{{ selectedRandomMessage }}</marquee>
    </v-col-md-6>
    <v-col-md-3>
      <h1 class="blink_text text-end frostie">FROSTIE.BAT</h1>
    </v-col-md-3>
  </v-row>
  <v-row>
    <v-col class="d-flex justify-center">
      <img class="text-center image" :src="selectedImage">
    </v-col>
  </v-row>
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
      {
        image: "https://media0.giphy.com/media/xT9KVHs6I3EfDKnVte/giphy.gif"
      },
      {
        image: "https://media.discordapp.net/attachments/236654120826699778/1163606388199665745/ezgif-2-7ab121e013.gif?ex=660b36e5&is=65f8c1e5&hm=629565f87b37f03e56ba8c0a0844bc53ff147c55f36fb8cc1d3422d91186ba87&"
      },
      {
        image: "https://media.discordapp.net/attachments/1120491072783667251/1165737684371787906/Tumblr_l_18254161065274.gif?ex=6609bd52&is=65f74852&hm=00ee9f6d942007d41ce3862cb85c746d1b65a6db8f689cb0ea3b7481d22347bc&"
      },
    ]);

    const messages = ref([
      {
        message: "YOU'VE BEEN PRANKED"
      },
      {
        message: "FROSTIE STRIKES AGAIN"
      },
      {
        message: "SUCKER SUCKER SUCKER"
      },
      {
        message: "FROSTIE STRIKES AGAIN"
      },
    ]);

    const selectedImage = ref('');
    const selectedRandomMessage = ref('');

    const selectRandomImage = () => {
      const randomIndex = Math.floor(Math.random() * images.value.length);
      selectedImage.value = images.value[randomIndex].image;
    };

    const selectRandomMessage = () => {
      const randomIndex = Math.floor(Math.random() * messages.value.length);
      selectedRandomMessage.value = messages.value[randomIndex].message;
    };

    onMounted(() => {
      selectRandomImage();
      selectRandomMessage();
    });

    return {
      selectedImage,
      selectRandomImage,
      selectedRandomMessage,
      selectRandomMessage
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

.frostie {
  margin-top: 60px;
  margin-right: 20px;
  margin-left: 20px;
}

.image {
  width: 100%;
  height: 79vh;
}

.blink_text {
  animation: 1s blinker linear infinite;
  -webkit-animation: 1s blinker linear infinite;
  -moz-animation: 1s blinker linear infinite;
  color: red;
}

@-moz-keyframes blinker {
  0% {
    opacity: 1.0;
  }

  50% {
    opacity: 0.0;
  }

  100% {
    opacity: 1.0;
  }
}

@-webkit-keyframes blinker {
  0% {
    opacity: 1.0;
  }

  50% {
    opacity: 0.0;
  }

  100% {
    opacity: 1.0;
  }
}

@keyframes blinker {
  0% {
    opacity: 1.0;
  }

  50% {
    opacity: 0.0;
  }

  100% {
    opacity: 1.0;
  }
}
</style>
