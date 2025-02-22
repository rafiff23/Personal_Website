<template>
  <div class="container mx-auto p-3 md:p-8">
    <div class="flex flex-col-reverse md:flex-row relative">
      <div class="w-full md:w-2/3">
        <div class="flex flex-col gap-4 md:px-20 fade-zoom-up">
          <div v-for="article in articles" 
            :key="article.id" 
            @click="openModal(article)"
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
          </div>
        </div>
      </div>
      <div class="w-full md:w-1/3 h-fit p-8 md:sticky md:top-24">
        <!-- Sidebar -->
        <div class="flex flex-col text-left">
          <div class="bg-clip-text bg-gradient-to-r from-slate-100 to-amber-300 text-transparent">These publications reflect my analytical approach to Computer Science.
          </div>
          <div class="h-[1px] mt-7 mb-7 w-20 bg-amber-200 aos-init aos-animate mr-2"></div>
          <div class="hidden md:block">
            <div class="text-white text-md font-semibold">Topics</div>
            <div class="mt-3 flex flex-wrap gap-1">
              <span
                class="py-2 px-3 rounded-2xl bg-[#1e1e1f] text-white text-xs cursor-pointer">Machine Learning</span>
              <span class="py-2 px-3 rounded-2xl bg-[#1e1e1f]  text-white text-xs cursor-pointer">Python</span>
              <span class="py-2 px-3 rounded-2xl bg-[#1e1e1f]  text-white text-xs cursor-pointer">R</span>
              <span class="py-2 px-3 rounded-2xl bg-[#1e1e1f]  text-white text-xs cursor-pointer">Chatbots</span>
              <span class="py-2 px-3 rounded-2xl bg-[#1e1e1f]  text-white text-xs cursor-pointer">Random Forest</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Article Modal -->
    <ArticleModal 
      v-if="selectedArticle" 
      :article="selectedArticle" 
      :isOpen="isModalOpen" 
      @close="closeModal" 
    />
  </div>
</template>

<script>
import ArticleModal from './ArticleModal.vue';

export default {
  components: {
    ArticleModal
  },
  data() {
    return {
      selectedArticle: null,
      isModalOpen: false,
      articles: [
        {
          id: "1",
          slug: "first-article",
          title: "Optimizing Concrete Strength Prediction: A Random Forest Approach with Hyperparameter Tuning through Random Search for Enhanced Construction Quality",
          desc: "Revolutionizing construction with AI: Our model predicts concrete strength with 90%+ accuracy and minimal error!",
          date: "ICICoS 2024",
          image: "https://ik.imagekit.io/fcuinpkmj/Screenshot%202025-02-23%20012943%20(3).png?updatedAt=1740251127420",
          content: "<p>In order to build stronger and longer-lasting structures, this study enhances concrete mix design with the use of machine learning. Highly accurate predictions were made using the Random Forest model, which attained an MAE below 4 and a R² above 90%. The results demonstrate its ability to improve building quality while minimising errors.</p>",
          demo: "https://www.researchgate.net/publication/383290176_Optimizing_Concrete_Strength_Prediction_A_Random_Forest_Approach_with_Hyperparameter_Tuning_through_Random_Search_for_Enhanced_Construction_Quality"
        },
        {
          id: "2",
          slug: "second-article",
          title: "Systematic Literature Review on Implementation of Chatbots for Commerce Use",
          desc: "Chatbots are revolutionising online shopping, they make customer contact more engaging, accurate, and user-friendly, just like a human.",
          date: "ICCSCI 2023",
          image: "https://ik.imagekit.io/fcuinpkmj/Screenshot%202025-02-23%20013327%20(1).png?updatedAt=1740251227228",
          content: "<p>More prospects for expansion over the internet have arisen as a result of companies' digitisation. Chatbots are becoming more popular as e-commerce solutions for organisations looking to increase client engagement. Chatbots have become easier to use, more accurate, and more lifelike thanks to technological advancements.</p>",
          demo: "https://www.researchgate.net/publication/375919599_Systematic_Literature_Review_on_Implementation_of_Chatbots_for_Commerce_Use"
        },
        {
          id: "3",
          slug: "third-article",
          title: "A Beginner’s Guide to Building Binary Search Trees in Python",
          desc: "Learn how Binary Search Trees (BST) enable fast lookups and master their implementation in this Medium post!",
          date: "Medium 2024",
          image: "https://miro.medium.com/v2/resize:fit:720/format:webp/1*_e_9HIsdwaBNGmQOCIbOyQ.jpeg",
          content: "<p>Has the lightning-fast operation of search engines or your phone's contact prediction ever baffled you? These fast lookups are made possible by the effective data architecture of Binary Search Trees (BST). Learn what BSTs are, what they mean, and how to use them in your own code in this article published on Medium.</p>",
          demo: "https://medium.com/@muhammadrafif3225/a-beginners-guide-to-building-binary-search-trees-in-python-b5bad0a4c022"
        }
      ]
    };
  },
  methods: {
    openModal(article) {
      this.selectedArticle = article;
      this.isModalOpen = true;
    },
    closeModal() {
      this.isModalOpen = false;
      this.selectedArticle = null;
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
