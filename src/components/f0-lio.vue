<template>
  <div class="bg-gradient-to-r from-zinc-900 to-slate-500 text-white h-screen w-full">
    <div>
      <header id="welcome-text" class="p-4 flex items-center justify-between">
        <div class="flex justify-start text-3xl font-normal space-x-1">
          <span>W</span>
          <span>E</span>
          <span>L</span>
          <span>C</span>
          <span>O</span>
          <span>M</span>
          <span>E</span>
        </div>

        <div class="flex space-x-10">
          <p v-for="item in ['Home', 'Projects', 'Contact', 'Options']" :key="item"
            class="animate-pulse duration-500 hover:text-blue-400 cursor-pointer">
            {{ item }}
          </p>
        </div>
      </header>


      <section class="flex flex-col justify-center items-center h-[80vh] space-y-6">
        <h1 class="text-6xl items-center" id="ff">Feel Free To Explore</h1>
        <h4 class="text-xl text-center max-w-2xl">Welcome to F0-Lio, your personal portfolio showcase. Explore my
          projects, skills, and experiences in one place.</h4>
        <PixelTeto class="mt-6 opacity-90 hover:scale-110 transition-transform" />
      </section>
    </div>
  </div>

</template>
<script>
import PixelTeto from '@/components/PixelTeto.vue'

export default {
  name: 'F0Lio',
  components: {
    PixelTeto
  }
}
</script>

<style scoped>
#ff {

  animation: shadow-dance 2s infinite;
}

@keyframes shadow-dance {
  0% {
    text-shadow: 0 0 5px #ff005e, 0 0 10px #ff005e, 0 0 20px #ff005e, 0 0 40px #ff005e;
  }

  100% {
    text-shadow: 0 0 10px #00d4ff, 0 0 20px #00d4ff, 0 0 40px #00d4ff, 0 0 80px #00d4ff;
  }
}

#welcome-text span {
  display: inline-block;
  animation: welcome 2s ease-in-out infinite;
}

#welcome-text span:nth-child(1) {
  animation-delay: 0s;
}

#welcome-text span:nth-child(2) {
  animation-delay: 0.2s;
}

#welcome-text span:nth-child(3) {
  animation-delay: 0.4s;
}

#welcome-text span:nth-child(4) {
  animation-delay: 0.6s;
}

#welcome-text span:nth-child(5) {
  animation-delay: 0.8s;
}

#welcome-text span:nth-child(6) {
  animation-delay: 1s;
}

#welcome-text span:nth-child(7) {
  animation-delay: 1.2s;
}

@keyframes welcome {

  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-10px);
  }
}
</style>