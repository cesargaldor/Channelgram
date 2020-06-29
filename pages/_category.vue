<template>
  <div>
    <nav class="w-full fixed h-16 items-center flex justify-between bg-white z-50">
      <div class>
        <nuxt-link
          to="/"
          class="atras flex sm:text-lg lg:text-xl xl:text-xl px-4 font-medium color"
        >←&nbsp;Back</nuxt-link>
      </div>
      <div class="h-full flex items-center">
        <nuxt-link to="/">
          <img src="@/static/icon.png" alt="logo" class="sm:w-8 lg:w-8" />
        </nuxt-link>
      </div>
      <div class="px-12"></div>
    </nav>

    <div class="font-medium bg-white w-full pt-32 pb-16 flex flex-col items-center">
      <span class="text-5xl">{{categoria.emoji}}</span>
      <h1 class="color text-3xl">{{categoria.titulo}}</h1>
    </div>

    <div class="w-full bg-gray-100 pt-6 pb-2">
      <a
        v-for="link in categoria.canales"
        :key="link.titulo"
        :href="link.url"
        target="_blank"
        rel="noopener"
        class="atras sm:mx-2 lg:mx-32 xl:w-4/6 xl:mx-auto flex py-8 border border-gray-300 mb-3"
      >
        <div
          class="flex items-center justify-center text-2xl sm:px-4 lg:px-8 xl:px-8"
        >{{categoria.emoji}}</div>
        <div class>
          <h1 class="font-medium">{{link.titulo}}</h1>
          <p class="text-gray-600">{{link.descripcion}}</p>
        </div>
      </a>
    </div>
    <contact />
  </div>
</template>

<script>
import contact from "@/components/contact.vue";
//import categories from "@/content/categories";
import data from "~/static/data.json";

export default {
  transition: "page",
  data() {
    return {
      //categories: categories.categories,
      name: this.$route.params.category
      //conjunto: []
    };
  },
  head() {
    return {
      title: "Channelgram ",
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
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
  },
  methods: {
    /*getConjunto() {
      var array = this.categories.filter(
        category => category.url == this.$route.params.category
      );
      this.conjunto = array;
    }*/
  },

  created() {
    //this.getConjunto();
  },

  computed: {
    categoria() {
      return data.find(el => el.url === this.name);
    }
  }
};
</script>

<style scoped>
nav {
  box-shadow: 0 4px 24px rgba(32, 43, 54, 0.08);
}

.atras {
  transition: 0.4s;
}
.atras:hover {
  transform: translateX(6px);
}
</style>