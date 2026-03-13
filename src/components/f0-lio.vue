<template>
  <div class="bg-[url('media/wpf.png')] bg-cover bg-center h-screen w-screen transition-all duration-100"
    :class="{ 'blur-sm grayscale': isOpen }">
    <!-- mañana veo -->
    <!-- <div class="bg-gradient-to-r from-zinc-900 to-slate-500 text-white h-screen w-full ">     <div :class="{ 'blur-sm grayscale transition-all': isOpen }">-->
    <div>
      <header class="p-4 flex items-center justify-between text-white">
        <div id="welcome-text" class="flex justify-start text-3xl font-thin space-x-1 text-white font-smash">
          <span>W</span>
          <span>E</span>
          <span>L</span>
          <span>C</span>
          <span>O</span>
          <span>M</span>
          <span>E</span>
        </div>



        <div class="flex space-x-7">
          <p v-for="item in ['Home', 'Projects', 'Contact', 'Options']" :key="item" v-on:click="navTo(item)"
            class=" duration-500 hover:text-blue-400 cursor-pointer font-smash text-[22px]">
            {{ item }}
          </p>
        </div>
      </header>


      <section class="flex flex-col justify-center items-center h-[80vh] space-y-6 " id="ww">
        <h1 class="text-7xl items-center font-jumbo text-white" id="ff">Feel Free To Explore</h1>
        <h4 id="h4i" class="text-4xl text-center max-w-6xl font-sans font-extrabold ">Hello!, this is my home. Now,
          it's yours. Feel
          free to experience every part of this place. Contact me if you need something, I always respond.</h4>
        <!-- <PixelTeto ref="tetoRef" id="pixel-teto" class="mt-6 opacity-100 hover:scale-110" /> -->
        <button @click="isOpen = true" class="bg-blue-500 text-white px-4 py-2 rounded">
          Abrir Modal
        </button>

      </section>
    </div>

    <button @click="isOpen = false" class="mt-4 text-red-500">Cerrar</button>
  </div>

</template>
<script>
import PixelTeto from '@/components/PixelTeto.vue'
import { animate, stagger, random, splitText, spring } from 'animejs'
import { ref } from 'vue';


export default {
  name: 'F0Lio',

  components: {
    PixelTeto
  },

  data() {
    return {
      navItems: ['Home', 'Projects', 'Contact', 'Options'],
      welcomeAn: null,
      tetoAn: null,
      animaOn: true,
      isOpen: false,
    }
  },

  mounted() {
    this.$nextTick(() => {
      console.log('MOUNTED pixel-teto')
      console.log()
      console.log("animations on", this.animaOn);
      const { chars } = splitText('#ff', { words: false, chars: true });

      this.welcomeAn = animate(
        '#welcome-text span',
        {
          keyframes: [
            {
              translateY: -10,
              rotate: '-3turn',
              easing: 'outExpo',
              duration: 600
            },
            {
              translateY: 0,
              easing: 'outBounce',
              duration: 800
            }
          ],
          delay: stagger(80),
          loop: true,
          loopDelay: 1000
        }
      ),
        this.tetoAn = animate('#pixel-teto', {
          keyframes: [
            { translateY: 10, duration: 1200, easing: 'easeInOutSine' },
            { translateY: 0, duration: 1200, easing: 'easeInOutSine' }
          ],
          loop: true
        })




      /*animate('#ww', {
        scale: 1.25,
        ease: spring({
          bounce: 0.5,
          duration: 628
        })
      });*/


    })

  },

  methods: {
    navTo(item) {
      console.log(`Navigating to: ${item.toLowerCase()}`)
    },
    offAnimation() {
      this.animaOn = !this.animaOn;
      console.log("ANIMA ON? ", this.animaOn);
      // const theAction = this.animaOn ? 'play' : 'pause';
      // this.welcomeAn?.[theAction]();
      // this.tetoAn?.[theAction]();

      if (this.animaOn === false) {
        animate('#welcome-text span', {
          keyframes: [
            {
              translateY: 0,
              rotate: 0,
              easing: 'outExpo',
              duration: 1
            },
            {
              translateY: 0,
              easing: 'outBounce',
              duration: 1
            }
          ],
          loop: false,
        }),
          animate('#pixel-teto', {
            keyframes: [
              {
                translateY: 0,
                rotate: 0,
                easing: 'outExpo',
                duration: 1
              },
              {
                translateY: 0,
                easing: 'outBounce',
                duration: 1
              }
            ],
            loop: false,
          });
      } else {
        animate('#pixel-teto', {
          keyframes: [
            { translateY: 10, duration: 1200, easing: 'easeInOutSine' },
            { translateY: 0, duration: 1200, easing: 'easeInOutSine' }
          ],
          loop: true
        }),
          animate(
            '#welcome-text span',
            {
              keyframes: [
                {
                  translateY: -10,
                  rotate: '-3turn',
                  easing: 'outExpo',
                  duration: 600
                },
                {
                  translateY: 0,
                  easing: 'outBounce',
                  duration: 800
                }
              ],
              delay: stagger(80),
              loop: true,
              loopDelay: 1000
            }
          )
      }

    }
  },

  computed: {
  }
}
</script>


<style scoped>
#ff {

  animation: shadow-dance 4s infinite;
}

@keyframes shadow-dance {
  0% {
    text-shadow: 0 0 10px #4ade80, 0 0 10px #4ade80, 0 0 20px #4ade80, 0 0 40px #4ade80;
  }

  50% {
    text-shadow: 0 0 5px #3245ce, 0 0 5px #3245ce, 0 0 10px #3245ce, 0 0 20px #3245ce;
  }

  100% {
    text-shadow: 0 0 10px #4ade80, 0 0 10px #4ade80, 0 0 20px #4ade80, 0 0 40px #4ade80;
  }
}

#h4i {
  text-shadow: 3.5px 0 5px #3fcc73;
  /* rgb(9, 67, 16) #4ade80*/
  color: #ffffff;
  animation: shadow-dance2 4s infinite;
}

@keyframes shadow-dance2 {
  0% {
    text-shadow: 0 0 2px #4ade80, 0 0 4px #4ade80, 0 0 6px #4ade80, 0 0 10px #4ade80;
  }

  50% {
    text-shadow: 0 0 2px #3245ce, 0 0 4px #3245ce, 0 0 6px #3245ce, 0 0 10px #3245ce;
  }

  100% {
    text-shadow: 0 0 2px #4ade80, 0 0 4px #4ade80, 0 0 6px #4ade80, 0 0 10px #4ade80;
  }
}
</style>