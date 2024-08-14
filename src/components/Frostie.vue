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
      <h1 class=" red ">
        I hope you are having a great {{ currentDay }} at {{ time }}
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
        <img class="movePaul image2" :src="paul2" alt="Paul">
    </v-col>
  </v-row>
  <v-row class="no-margin height: -10px;">
    <v-col style="max-height: 20px" v-for="(banner, index) in shuffledBanners" :key="index" class="no-margin">
      <img class="no-margin banner-image" :src="banner.src">
    </v-col>
  </v-row>
</template>

<script setup>
import { ref, onMounted } from 'vue';
const pc = 'I am inside your PC :)';

const paul2 = ref('./images/paul2.jpg')

const images = ref([
  // {
  //   image: '../../src/assets/me.gif'
  // },
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
  // {
  //   image: '../../src/assets/trollface-horror.gif'
  // },
  // {
  //   image: '../../src/assets/Tumblr_l_18254161065274.gif'
  // },
  // {
  //   image: '../../src/assets/maltigi-scary.gif'
  // },
  // {
  //   image: '../../src/assets/image0-15.gif'
  // },
  // {
  //   image: '../../src/assets/ezgif-2-7ab121e013.gif'
  // },
  {
    image: './images/paul.jpg'
  }
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

const selectedImage = ref('');
const selectedRandomMessage = ref('');
const shuffledBanners = ref([]);
const time = ref(0);
const currentDay = ref();


const updateCurrentDay = async () => {
  setInterval(() => {
    const currentDate = new Date();
    const daysOfWeek = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];

    const currentTime = currentDate.getTime();
    const currentDayOfWeek = daysOfWeek[currentDate.getDay() - 1];
    time.value = convertTime(currentTime);
    currentDay.value = currentDayOfWeek;
  }, 1);
};

const convertTime = (time) => {
  const date = new Date(time);
  const hours = date.getHours() % 12 || 12;
  const minutes = date.getMinutes().toString().padStart(2, '0');
  const seconds = date.getSeconds().toString().padStart(2, '0');
  const ampm = date.getHours() < 12 ? 'AM' : 'PM';
  return `${hours}:${minutes}:${seconds} ${ampm}`;
}


const selectRandomImage = async () => {
  const randomIndex = Math.floor(Math.random() * images.value.length);
  selectedImage.value = images.value[randomIndex].image;
  console.log(images.value[randomIndex].image);
};

const selectRandomMessage = async () => {
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

const selectRandomBanners = async () => {
  shuffledBanners.value = shuffleArray(banners.value).slice(0, 3);
};

onMounted(async () => {
  await selectRandomImage();
  await selectRandomMessage();
  await selectRandomBanners();
  await updateCurrentDay();
});
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

.red {
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

.movePaul {
  position: absolute;
  top: 100px;
  left: 50%;
  width: 500px;
  height: 1500px;
  animation: moveInCircle 5s linear infinite;
  z-index: 20;
}

@keyframes moveInCircle {
  from {
    transform: rotate(0deg) translateX(100px) rotate(0deg);
  }
  to {
    transform: rotate(360deg) translateX(100px) rotate(-360deg);
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
