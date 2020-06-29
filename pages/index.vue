<template>
  <div class="min-h-screen bg-gray-100">
    <div class="bg-white flex flex-col items-center justify-center w-full py-5">
      <img src="@/static/icon.png" alt="logo" class="pt-10 sm:w-12 lg:w-16 xl:w-20" />
      <h1 class="font-medium text-3xl mb-1 mt-1 color">Channelgram</h1>
      <p
        class="pb-12 font-thin text-xl text-gray-600 sm:px-10 sm:text-center"
      >Colección de canales de todo tipo de temáticas.</p>
    </div>
    <div class="sm:w-full lg:w-full lg:w-10/12 xl:w-9/12 xl:mx-auto mb-10 pt-6 pb-5">
      <h1 class="mt-8 text-center font-medium text-2xl mb-1 color">Categorías</h1>
      <p
        class="text-center font-thin text-base text-gray-600"
      >Descubre multitud de canales en cada categoría</p>
      <div
        class="grid sm:grid-cols-2 lg:grid-cols-6 xl:grid-cols-6 sm:gap-5 lg:gap-4 xl:gap-6 mt-8 sm:px-5 lg:px-6"
      >
        <nuxt-link
          v-for="category in data"
          :key="category.emoji"
          :to="`/${category.url}`"
          class="categoria bg-white flex flex-col items-center py-10 rounded border border-gray-200"
        >
          <span class="text-3xl pb-2">{{category.emoji}}</span>
          <h3 class="text-lg">{{category.titulo}}</h3>
        </nuxt-link>
      </div>
      <!-- Div para publicidad
      <div class="w-full h-56 mt-6 mb-6 bg-red-300">HOLA</div>
      -->
    </div>
    <contact />
  </div>
</template>

<script>
import contact from "@/components/contact.vue";
//import categories from "@/content/categories";
import data from "~/static/data.json";

export default {
  name: "index",
  transition: "page",
  data() {
    return {
      //categories: categories.categories,
      data: data
    };
  },
  head() {
    return {
      title: "Channelgram",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Your web to discover new telegram channels"
        }
      ]
    };
  },

  components: {
    contact
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500;700;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Rubik", sans-serif;
}

.color {
  background: #41b883;
  background: -webkit-linear-gradient(to left, #41b883, #309668);
  background: linear-gradient(to left, #41b883, #309668);
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.boton {
  background: #41b883;
  background: -webkit-linear-gradient(to left, #41b883, #309668);
  background: linear-gradient(to left, #41b883, #309668);
}

.categoria {
  transition: 0.3s;
}

.categoria:hover {
  transform: translateY(-8px);
  box-shadow: 0 0.5em 0.5em -0.4em rgba(0, 0, 0, 0.055);
}

.page-enter-active,
.page-leave-active {
  transition-property: opacity;
  transition-timing-function: ease-in-out;
  transition-duration: 300ms;
}
.page-enter,
.page-leave-to {
  opacity: 0;
}
</style>
