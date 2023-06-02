<template>
    <div class="container my-20 px-6 mx-auto">
      <h2 class="text-3xl font-bold mb-4">Products</h2>
      <p class="mb-7 text-gray-500">
        this is the best product from our store please try it guaranteed you won't regret it
      </p>
      <section class="text-gray-800">

        <div class="flex flex-wrap grid sm:container xs:grid-cols-3 sm:grid-cols-3 md:grid-cols-3 lg:grid-cols-3 gap-8 xl:gap-x-12">
          <div v-for="(product, index) in count.products" :key="index">
            <div id="default-carousel" class="relative w-full h-full" data-carousel="slide">
            <div class="relative h-56 overflow-hidden rounded-lg">
                <div class="hidden duration-400 ease-in-out" v-for="(image, index) in product.images" :key="index" data-carousel-item>
                    <img :src="image" class="absolute block w-full h-full -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2">
                </div>
            </div>
            <div class="mt-4">
              <div class="flex justify-between">
                          <p class="font-bold text-lg">{{ product.title }}</p>
                          <span><ul class="flex justify-center">
                            <li>
                              <svg
                                xmlns="http://www.w3.org/2000/svg"
                                viewBox="0 0 24 24"
                                fill="currentColor"
                                class="mr-1 mt-0 h-5 w-5 text-warning">
                                <path
                                  fill-rule="evenodd"
                                  d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.007 5.404.433c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.433 2.082-5.006z"
                                  clip-rule="evenodd" />
                              </svg>
                            </li>
                            <li>
                              {{ product.rating }}
                            </li>
                          </ul></span>
            </div>
            <p class="text-gray-500">{{ product.brand }}</p>
                        <p class="text-gray-500 mb-3">
                          {{ product.category }}
                        </p>
                        <p class="font-bold text-lg mb-4">${{ product.price }} <span class="font-normal text-gray-500"></span></p>
                        <NuxtLink class="inline-block px-7 py-3 mr-2 bg-orange-500 text-white font-medium text-sm leading-snug uppercase rounded-lg shadow-md hover:bg-rose-700 hover:shadow-lg focus:bg-rose-700 focus:shadow-lg focus:outline-none focus:ring-0 active:bg-rose-800 active:shadow-lg transition duration-150 ease-in-out" data-mdb-ripple="true" data-mdb-ripple-color="light" :to="'/product/' + product.id" role="button">Detail Product</NuxtLink>
            </div>
            </div>
          </div>
        </div>

      </section>
    </div>
</template>
    
<script setup>
import { onMounted } from 'vue'
import { 
    initAccordions, 
    initCarousels, 
    initCollapses, 
    initDials, 
    initDismisses, 
    initDrawers, 
    initDropdowns, 
    initModals, 
    initPopovers, 
    initTabs, 
    initTooltips } from 'flowbite'

// initialize components based on data attribute selectors
onMounted(() => {
    initAccordions();
    initCarousels();
    initCollapses();
    initDials();
    initDismisses();
    initDrawers();
    initDropdowns();
    initModals();
    initPopovers();
    initTabs();
    initTooltips();
})

const {pending, data: count} = await useFetch('https://dummyjson.com/products', {
  lazy: true
})
</script>

<style scoped>
  body {
    background-color: hsl(0, 0%, 97%)
  }
</style>

<!-- <script setup>
const runTimeConfig = useRuntimeConfig();

const products = ref([])
onMounted(()=>{
  fetch(`${runTimeConfig.public.baseUrl}/products`, {
    headers: {
      Authorization: `Bearer ${runTimeConfig.public.appSecret}`,
    },
  }).then(res => res.json()).then(data => products.value = data);
});
</script> -->

<!-- <script setup>

const runtimeConfigs = useRuntimeConfig()
const page = ref(1)

const {data: products, pending, refresh} = await useFetch(()=>`${runtimeConfigs.public.API_URL}/products?page=${page.value}`, {
    key: `productlist-${page.value}`,
})

function refetch(pageNumber){
    page.value = pageNumber
    refresh()
}

</script> -->

<!-- <script setup>
const { data: products } = await useFetch('https://dummyjson.com/products?limit=12')
</script> -->