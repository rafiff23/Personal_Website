<template>
  <main
    class="mt-10 md:mt-1 flex flex-col-reverse gap-8 items-center md:flex-row md:gap-16 md:justify-center min-h-[65vh] md:min-h-[80vh]">
    <div class="space-y-2 text-center md:text-left px-10">
      <p class="text-amber-200">Hello World, I'm</p>
      <h1 class="text-4xl font-bold md:text-5xl text-white fadein-up">Muhammad Rafif</h1>
      <div class="py-2">
        <h1
          class="typewrite text-xl font-semibold text-transparent bg-clip-text bg-gradient-to-r from-slate-100 to-yellow-500 md:text-2xl fadein-up"
          ref="typewriter">
          <span class="wrap">{{ txt }}</span>
        </h1>
      </div>
      <p class="text-white pr-4 fade-in-from-left">Welcome to My personal website. <span class="wave">👋🏼</span></p>
      <div class="flex md:order-2 fadein-bot space-x-4">
          <a href="https://github.com/rafiff23" target="_blank"><img class="w-9 rounded-full" src="https://seeklogo.com/images/G/github-logo-2E3852456C-seeklogo.com.png" alt="github"></a>
          <a href="https://www.researchgate.net/profile/Muhammad-Rafif-13?ev=hdr_xprf" target="_blank"><img class="w-9 rounded-full" src="data:image/png;base64,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" alt="ResearchGate"></a>
          <a href="https://www.linkedin.com/in/muhammad-rafif-838938232/" target="_blank"><img class="w-9 rounded-full" src="https://img.icons8.com/?size=100&id=60444&format=png&color=FFFFFF" alt="LinkedIn"></a>
      </div>
      <br>
      <button
        class="fadein-bot fade-500 flex items-center py-2 px-4 mx-auto text-sm font-medium rounded-lg border transition duration-300 md:py-2.5 md:px-5 md:mx-0 text-amber-200 border-amber-200 hover:bg-amber-200 hover:bg-opacity-10 bg-transparent focus:outline-none w-fit"><svg
          xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="mr-2 w-4 h-4">
          <path fill-rule="evenodd"
            d="M5.625 1.5H9a3.75 3.75 0 013.75 3.75v1.875c0 1.036.84 1.875 1.875 1.875H16.5a3.75 3.75 0 013.75 3.75v7.875c0 1.035-.84 1.875-1.875 1.875H5.625a1.875 1.875 0 01-1.875-1.875V3.375c0-1.036.84-1.875 1.875-1.875zm5.845 17.03a.75.75 0 001.06 0l3-3a.75.75 0 10-1.06-1.06l-1.72 1.72V12a.75.75 0 00-1.5 0v4.19l-1.72-1.72a.75.75 0 00-1.06 1.06l3 3z"
            clip-rule="evenodd"></path>
          <path
            d="M14.25 5.25a5.23 5.23 0 00-1.279-3.434 9.768 9.768 0 016.963 6.963A5.23 5.23 0 0016.5 7.5h-1.875a.375.375 0 01-.375-.375V5.25z">
          </path>
        </svg>Download Resume</button>
    </div>
    <div class="flex justify-center md:justify-start fadein-right"><img alt="avatar" fetchpriority="high" width="300" height="300" decoding="async" data-nimg="1"
        class="w-10/12 md:h-auto rounded-full border-4 border-amber-200 pict" src="https://ik.imagekit.io/fcuinpkmj/12.JPG?updatedAt=1740054785328">
    </div>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      toRotate: ["Data Scientist", "Data Analyst", "Informatics Student", "Data Engineer", "Data Enthusiast"],
      period: 2000,
      txt: '',
      loopNum: 0,
      isDeleting: false,
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.tick();
    });
  },
  methods: {
    tick() {
      let typewriter = this.$refs.typewriter;

      if (!typewriter) {
        return;
      }

      let i = this.loopNum % this.toRotate.length;
      let fullTxt = this.toRotate[i];

      this.txt = this.isDeleting ? fullTxt.substring(0, this.txt.length - 1) : fullTxt.substring(0, this.txt.length + 1);
      typewriter.innerHTML = `<span class="wrap">${this.txt}</span>`;

      let that = this;
      let delta = 200 - Math.random() * 100;

      if (this.isDeleting) {
        delta /= 2;
      }

      if (!this.isDeleting && this.txt === fullTxt) {
        delta = this.period;
        this.isDeleting = true;
      } else if (this.isDeleting && this.txt === '') {
        this.isDeleting = false;
        this.loopNum++;
        delta = 500;
      }

      setTimeout(() => {
        that.tick();
      }, delta);
    },
  }
}
</script>

<style>
body {
  overflow-y: scroll;
  overflow-x: hidden;
}

.typewrite>.wrap {
  border-right: 0.08em solid #fff;
}

.wave {
  animation-name: wave-animation;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  transform-origin: 70% 70%;
  display: inline-block
}

@keyframes wave-animation {
  0% {
    transform: rotate(0deg)
  }

  10% {
    transform: rotate(14deg)
  }

  20% {
    transform: rotate(-8deg)
  }

  30% {
    transform: rotate(14deg)
  }

  40% {
    transform: rotate(-4deg)
  }

  50% {
    transform: rotate(10deg)
  }

  60% {
    transform: rotate(0deg)
  }

  to {
    transform: rotate(0deg)
  }
}

.pict {
  box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
-webkit-box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
-moz-box-shadow: 0px 0px 73px -9px rgba(255,219,112,0.44);
}

.fadein-up {
  opacity: 0;
  animation-name: fadeInUp;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;
  animation-delay: 500ms;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.fade-in-from-left {
  opacity: 0;
  animation: fadeInLeft 0.5s ease-out forwards;
  animation-delay: 500ms;
}

@keyframes fadeInLeft {
  0% {
    opacity: 0;
    transform: translateX(-100%);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadein-right {
  opacity: 0;
  animation: fadeInRight 0.5s ease-out forwards;
  animation-delay: 500ms;
}

@keyframes fadeInRight {
  0% {
    opacity: 0;
    transform: translateX(100%);
  }
  100% {
    opacity: 1;
    transform: translateX(0);
  }
}

.fadein-bot {
  opacity: 0;
  animation: fadeInBot 0.5s forwards;
}

@keyframes fadeInBot {
  from {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.fadein-1 {
  animation-delay: 200ms;
}
.fadein-2 {
  animation-delay: 400ms;
}
.fadein-3 {
  animation-delay: 600ms;
}
.fade-500 {
  animation-delay: 500ms;
}
</style>
