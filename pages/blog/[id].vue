<script setup lang="ts">
const route = useRoute();

const { data: product, pending } = await useFetch(
  `https://www.itgenius.co.th/sandbox_api/mrta_flutter_api/public/api/news/${route.params.id}`
);

useHead({
  title: "บล็อก",
  meta: [
    {
      name: `${product.value.topic}`,
      content:`${product.value.topic}, Nuxt 3, Backend`,
    },
    {
      name: "Description",
      content: `${product.value.topic},  IT Genius Engineering`,
    },
  ],
});

</script>
<template>
  <div class="mt-5">
    <div class="wrapper">
      <v-row justify="center">
        <v-col cols="12" sm="10" md="9" lg="7">
          <div class="text-center">
            <h2 class="ui-title font-weight-bold text-white mb-4">
                {{ product.topic }}
            </h2>
          </div>
        </v-col>
      </v-row>
    </div>
    <ClientOnly>
    <v-container>
  
        <img :src="product.imageurl" alt="" class="w-100">
        <h3>{{ product.detail }}</h3>
        <p>{{ product.created_at }}</p>
       
    </v-container>
</ClientOnly>
  </div>
</template>

<style scoped>
.ui-title {
  font-size: 32px;
}

.font-18 {
  font-size: 18px;
}

.wrapper {
  background: #2196f3;
  padding: 40px 0 20px;
  min-height: 250px;
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.blog-card {
  transition: 0.2s ease-in;
}

.blog-card:hover {
  transform: translateY(-10px);
}

.blog-title {
  color: #263238 !important;
  line-height: 22px;
  font-weight: bold;
}

.blog-title:hover {
  color: #607df9 !important;
}
</style>
