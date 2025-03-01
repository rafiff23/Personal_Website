<template>
    <div v-if="isOpen" class="modal-overlay" @click="closeModal">
      <div @click.stop>
        <!-- Close Button -->

  
        <!-- Article Content -->
        <article class="bg-white rounded-lg p-8 w-full max-w-4xl mx-auto">
          <button 
            @click="closeModal" 
            class="absolute top-4 right-4 bg-black bg-opacity-60 text-white rounded-full p-2 transition duration-300 hover:bg-opacity-80 hover:scale-110"
          >
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="w-4 h-4">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
          <h1 class="text-xl md:text-4xl text-black text-left font-bold leading-relaxed">{{ article.title }}</h1>
          <!-- Description -->
          <div class="mt-3 text-left text-gray-800 text-sm">Published at <span>{{ article.date }}</span></div>
          <div class="h-[2px] w-20 my-5 md:my-10 bg-[#ffdb70] md:w-1/3 aos-init aos-animate mr-2"></div>
          <div>
            <div class="relative w-full" style="padding-top: 50%;">
                <img :src="article.image" class="absolute top-0 left-0 rounded-lg w-full h-full object-cover"
                    alt="Thumbnail">
            </div>
          </div>
          <!-- Full Content -->
          <div class="text-left text-black mt-8" v-html="article.content"></div>
  
          <!-- Icons Section -->
          <div class="mt-6 flex justify-end gap-4">
            <a v-if="article.demo" 
               :href="article.demo" 
               target="_blank" 
               rel="noopener noreferrer" 
               class="text-gray-600 hover:text-gray-900"
               @click.stop 
            >
              <svg stroke="currentColor" fill="none" stroke-width="2" viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round" height="24" width="24" xmlns="http://www.w3.org/2000/svg">
                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                <polyline points="15 3 21 3 21 9"></polyline>
                <line x1="10" y1="14" x2="21" y2="3"></line>
              </svg>
            </a>
          </div>
        </article>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      article: {
        type: Object,
        required: true
      },
      isOpen: {
        type: Boolean,
        required: true
      }
    },
    methods: {
      closeModal() {
        this.$emit('close');
      }
    }
  };
  </script>
  
  <style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  padding: 1rem; /* Ensures spacing on small screens */
}

article {
  background-color: white;
  padding: 2rem;
  border-radius: 0.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  position: relative;
  padding-bottom: 60px;
  
  /* Make modal responsive */
  width: 90%;
  max-width: 800px; /* Limits max size on large screens */
  max-height: 90vh; /* Prevents overflowing on small screens */
  overflow-y: auto; /* Enables scrolling when content is too large */
}

/* Adjust image responsiveness */
/* article img {
  max-width: 100%;
  height: auto;
  display: block;
} */

/* Adjust close button for smaller screens */
@media (max-width: 600px) {
  .close-button {
    top: 10px;
    right: 10px;
    font-size: 24px;
  }
}

  </style>