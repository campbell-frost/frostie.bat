<template>
  <v-row class="d-flex justify-center" style="height: 0px;">
    <v-col-md-2 class="frostie z">
      <h1 class="blink-text">FROSTIE.BAT</h1>
    </v-col-md-2>
    <v-col-md-8 class="z">
      <marquee scrollamount="100" class="marquee">
        {{ selectedRandomMessage }}
      </marquee>
      <h1 class="align-center red blink-text">
        {{ pc }}

      </h1>
    </v-col-md-8>
    <v-col-md-2 class="z">
      <h1 class="blink-text text-center frostie z">FROSTIE.BAT</h1>
    </v-col-md-2>
  </v-row>

  <v-row>
    <v-col class="d-flex justify-center no-margin">
      <img class="text-center image1" :src="selectedImage">
      <img class="image2 move"
        src="https://cdnb.artstation.com/p/assets/images/images/052/295/993/original/william-jacob-esqueleto-run-gif.gif?1659446940"
        style="animation: cubic-bezier(1,.51,1,1) move 5s infinite; z-index: 1">
    </v-col>
  </v-row>
  <v-row class="no-margin height: -10px;">
    <v-col style="max-height: 20px" v-for="(banner, index) in shuffledBanners" :key="index" class="no-margin">
      <img class="no-margin banner-image" :src="banner.src">
    </v-col>
  </v-row>
</template>

<script>
import { ref, onMounted } from 'vue';
export default {
  setup() {
    const pc = 'I am inside your PC :)'
    const date = new Date().getDate();

    const images = ref([
      {
        image: 'https://pouch.jumpshare.com/preview/AVgYbxEsXo4hVpiO0qmrgjLhWS5apzenbIcGsMQLswI204r8aVNooBNiKTBLnOJAKCIAoomIlUt0Pnids_pG2ec2FxZU1y6fV7HK6wdDD2U'
      }
      // {
      //   image: "https://i.etsystatic.com/5175241/r/il/ed217b/996818704/il_fullxfull.996818704_3vau.jpg",
      // },
      // {
      //   image: "https://media.tenor.com/HUz1LwDn_lAAAAAM/smile.gif"
      // },
      // {
      //   image: "https://media0.giphy.com/media/xT9KVHs6I3EfDKnVte/giphy.gif"
      // },
      // {
      //   image: "https://media1.tenor.com/m/ydDMqtC9kZEAAAAC/keanu-reeves.gif"
      // },
      // {
      //   image: "https://www.icegif.com/wp-content/uploads/2023/02/icegif-1690.gif"
      // },

      // {
      //   image: "https://image.emojipng.com/985/12350985.jpg"
      // },

    ]);

    const messages = ref([
      {
        message: `Good Morning Amy!`
      },
      // {
      //   message: "FROSTIE STRIKES AGAIN"
      // },
      // {
      //   message: "YOU'VE BEEN FROSTIED"
      // },
      // {
      //   message: "SUCKER SUCKER SUCKER"
      // },
      // {
      //   message: "GOTCHA GOTCHA GOTCHA"
      // },
    ]);

    const banners = ref([
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/at-t-the-first-banner-1994.png"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/windows-95-1996.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/internet-explorer-3-0-1996.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/ncaa-march-madness-1999.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/macromedia-flash-3-1998.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/microsoft-1999.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/coolsavings-1999.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/msn-1999.jpg"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/volkswagen-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/hp-shopping-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/ebay-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/hotmail-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/amazon-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/altavista-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/elle-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/buy-com-2000.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/netscape-netcenter-personal-finance-1999.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/lowest-fare-1999.gif"
      },
      {
        src: "https://www.webdesignmuseum.org/uploaded/exhibitions/web-banners-in-the-90s/mac-mall-1998.gif"
      },
    ]);
    const mailSound = ref(null);
    const audioSrc = "./public/yougotmail.mp3";

    const selectedImage = ref('');
    const selectedRandomMessage = ref('');
    const shuffledBanners = ref([]);

    const selectRandomImage = () => {
      const randomIndex = Math.floor(Math.random() * images.value.length);
      selectedImage.value = images.value[randomIndex].image;
    };

    const selectRandomMessage = () => {
      const randomIndex = Math.floor(Math.random() * messages.value.length);
      selectedRandomMessage.value = messages.value[randomIndex].message;
    };

    const shuffleArray = (array) => {
      const shuffled = array.slice();
      for (let i = shuffled.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
      }
      return shuffled;
    };

    const selectRandomBanners = () => {
      shuffledBanners.value = shuffleArray(banners.value).slice(0, 3);
    };

    onMounted(() => {
      selectRandomImage();
      selectRandomMessage();
      selectRandomBanners();

      mailSound.value = new Audio(audioSrc);
      mailSound.value.play();
    });

    return {
      selectedImage,
      selectRandomImage,
      selectedRandomMessage,
      selectRandomMessage,
      shuffledBanners,
      mailSound,
      pc,
    };
  },
};
</script>

<style>
.no-margin {
  margin-top: 0px !important;
  margin-bottom: 0px !important;
  padding-top: 0px !important;
  padding-bottom: 0px !important;
  margin-left: 0px !important;
  margin-right: 0px !important;
  padding-left: 0px !important;
  padding-right: 0px !important;
}

.marquee {
  font-size: 100px;
  color: red;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
}

.red{
  color: red;
  margin-top: 300px;
  font-size: 100px;
}

.z {
  z-index: 20;
}

.frostie {
  margin-top: 60px;
  margin-right: 20px;
  margin-left: 20px;
}

.image1 {
  position: relative;
  width: 100%;
  height: 93vh;
}

.image2 {
  left: 0px;
  position: absolute;
  top: 500px;
}

.blink-text {
  animation: 1s blinker linear infinite;
  -webkit-animation: 1s blinker linear infinite;
  -moz-animation: 1s blinker linear infinite;
  color: red;
  font-weight: bolder;
}

.banner-image {
  width: 100%;
}

@keyframes move {
  from {
    left: 0;
    transform: scale(1);
  }

  to {
    left: 70%;
    transform: scale(3.5);
  }
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
