<template>
    <div class="w-full md:w-3/5 h-20 mx-auto md:mt-5">
        <div class="bg-white rounded-xl mx-3 p-5 md:p-10 md:mx-0">
            <div>
                <h1 class="text-xl md:text-4xl text-black text-left font-bold leading-relaxed">{{ title }}</h1>
                <div class="mt-3 text-left text-gray-800 text-sm">Published at <span>{{ date }}</span></div>
                <div class="h-[2px] w-20 my-5 md:my-10 bg-[#ffdb70] md:w-1/3 aos-init aos-animate mr-2"></div>
                <div>
                    <div class="relative w-full" style="padding-top: 50%;">
                        <img :src="image" class="absolute top-0 left-0 rounded-lg w-full h-full object-cover"
                            alt="Thumbnail">
                    </div>
                </div>
                <div class="text-left text-black mt-8" v-html="content">
                    
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { useRoute } from 'vue-router';

export default {
  data() {
    return {
      route: useRoute(),
      title: '',
      image: '',
      date: '',
      content: '',
      articles: [
        {
          id: "1",
          slug: "first-article",
          title: "Optimizing Concrete Strength Prediction: A Random Forest Approach with Hyperparameter Tuning through Random Search for Enhanced Construction Quality",
          desc: "This is a sample article description.",
          date: "ICICoS 2024",
          image: "https://ik.imagekit.io/fcuinpkmj/Screenshot%202025-02-21%20040808.png",
          content: "<p>Full content of the first article goes here...</p>"
        },
        {
          id: "2",
          slug: "second-article",
          title: "Systematic Literature Review on Implementation of Chatbots for Commerce Use",
          desc: "This is another article description.",
          date: "ICCSCI 2023",
          image: "https://ik.imagekit.io/fcuinpkmj/image(1).png",
          content: "<p>Full content of the second article goes here...</p>"
        }
      ]
    };
  },
  mounted() {
    this.getDetails(); // Fetch article details on component mount
  },
  methods: {
    getDetails() {
      const id = this.route.params.id; // Get the article ID from the URL
      const article = this.articles.find(item => item.id === id); // Find the matching article by ID

      if (article) {
        this.title = article.title;
        this.image = article.image;
        this.date = article.date;
        this.content = article.content;
      } else {
        console.error("Article not found");
      }
    }
  }
};
</script>


<style scoped></style>