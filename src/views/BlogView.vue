<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col-reverse md:flex-row relative">
      <div class="w-full md:w-2/3">
        <div class="flex flex-col gap-4 md:px-20 fade-zoom-up">
          <!-- Wrap the entire article in router-link -->
          <router-link v-for="article in articles" 
            :key="article.id" 
            :to="`/read/${article.slug}/${article.id}`" 
            class="block"
          >
            <article class="bg-[#1e1e1f] border-[#383838] rounded-xl p-5 md:py-7 md:px-8 text-white hover:bg-[#282828] cursor-pointer relative">
              <div class="flex">
                <div class="flex-1 pr-4">
                  <div class="text-xs mb-1 text-slate-400 flex items-center italic">
                    <div class="h-[1px] w-20 bg-amber-200 md:w-5 mr-2"></div>
                    {{ article.date }}
                  </div>
                  <h1 class="text-sm md:text-md text-amber-200 font-bold mb-2 text-left">{{ article.title }}</h1>
                  <div class="text-sm hidden md:block text-left">{{ article.desc }}</div>
                </div>
                <div class="w-28 h-28 flex items-center">
                  <img :src="article.image" class="rounded-lg md:rounded-xl" alt="Article Image">
                </div>
              </div>

              <!-- Icons Section -->
              <div class="absolute bottom-4 right-4 flex gap-4">
                <!-- Demo Link for Read More -->
                <a v-if="article.demo" 
                   :href="article.demo" 
                   target="_blank" 
                   rel="noopener noreferrer" 
                   class="hover:text-gray-300"
                   @click.stop 
                >
                  <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="20" width="20" xmlns="http://www.w3.org/2000/svg">
                    <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                    <polyline points="15 3 21 3 21 9"></polyline>
                    <line x1="10" y1="14" x2="21" y2="3"></line>
                  </svg>
                </a>
              </div>
            </article>
          </router-link>
        </div>
      </div>
      <div class="w-full md:w-1/3 h-fit p-8 md:sticky md:top-24">
        <!-- Sidebar -->
          <div class="flex flex-col text-left">
            <div class="bg-clip-text bg-gradient-to-r from-slate-100 to-amber-300 text-transparent">Let's share experiences,
              stories, and knowledge together.
            </div>
            <div class="h-[1px] mt-7 mb-7 w-20 bg-amber-200 aos-init aos-animate mr-2"></div>
            <div class="hidden md:block">
              <div class="text-white text-md font-semibold">Topics</div>
              <div class="mt-3 flex flex-wrap gap-1">
                <span
                  class="py-2 px-3 rounded-2xl bg-[#1e1e1f] hover:bg-white/20 text-white text-xs cursor-pointer">NodeJS</span>
                <span
                  class="py-2 px-3 rounded-2xl bg-[#1e1e1f] hover:bg-white/20 text-white text-xs cursor-pointer">Technology</span>
              </div>
              <!-- <div class="h-[1px] mt-7 mb-7 w-20 bg-amber-200 aos-init aos-animate mr-2"></div> -->
              <!-- <div class="text-white text-md font-semibold">Popular Articles</div> -->

            </div>
          </div>
        </div>
    </div>
  </div>
</template>




<script>
import { useRoute, useRouter } from 'vue-router';

export default {
  data() {
    return {
      route: useRoute(),
      router: useRouter(),
      title: '',
      image: '',
      date: '',
      content: '',
      github: '',
      demo: '',
      articles: [
        {
          id: "1",
          slug: "first-article",
          title: "Optimizing Concrete Strength Prediction: A Random Forest Approach with Hyperparameter Tuning through Random Search for Enhanced Construction Quality",
          desc: "This is a sample article description.",
          date: "ICICoS 2024",
          image: "https://ik.imagekit.io/fcuinpkmj/Screenshot%202025-02-21%20040808.png",
          content: "<p>Full content of the first article goes here...</p>",
          github: "https://github.com/rafiff23/HumanResource-ShinyWebApp",
          demo: "https://rafif.shinyapps.io/HumanResource/"
        },
        {
          id: "2",
          slug: "second-article",
          title: "Systematic Literature Review on Implementation of Chatbots for Commerce Use",
          desc: "This is another article description.",
          date: "ICCSCI 2023",
          image: "https://ik.imagekit.io/fcuinpkmj/image(1).png",
          content: "<p>Full content of the second article goes here...</p>",
          github: "",
          demo: ""
        }
      ]
    };
  },
  mounted() {
    this.getDetails();
  },
  methods: {
    getDetails() {
      const id = this.route.params.id;
      const article = this.articles.find(item => item.id === id);

      if (article) {
        this.title = article.title;
        this.image = article.image;
        this.date = article.date;
        this.content = article.content;
        this.github = article.github;
        this.demo = article.demo;
      } else {
        console.error("Article not found");
      }
    },
    goBack() {
      this.router.push("/blog"); // Change to your actual blog list route
    }
  }
};
</script>

<style scoped>
.paraf {
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
  overflow: hidden;
}
@media (min-width: 768px) { 
  .paraf {
    display: -webkit-box;
  }
}
@keyframes fadeZoomUp {
  0% {
    opacity: 0;
    transform: scale(0.5);
  }
  100% {
    opacity: 1;
    transform: scale(1);
  }
}
.fade-zoom-up {
  animation: fadeZoomUp 1s ease-in-out;
}

article {
  position: relative;
  padding-bottom: 60px; /* Add padding to make room for buttons */
}

button {
  display: flex;
  align-items: center;
}

button .material-icons-outlined {
  font-size: 18px;
}

button svg {
  height: 16px;
  width: 16px;
}

</style>  
