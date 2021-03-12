<template>

        <div class=" md:flex w-screen bg-no-repeat bg-cover " style="height:60vh;"   v-bind:style="{ 'background-image': 'url(http://localhost:1337'+ hero.background.url + ')' }">
        <div class="w-screen bg-black absolute z-0 opacity-50" style="height:60vh"></div>
          
            <div class="container px-6 pt-20 md:py-3 mx-auto md:flex md:justify-between md:items-center relative">
                <div class="max-w-xl">
                    <h2 class="text-4xl font-semibold text-white dark:text-white md:text-5xl">{{hero.title}} </h2>
                    <p class="mt-2 text-sm text-white dark:text-gray-400 md:text-base">{{hero.short}}</p>

                    <div class="flex mt-6">
                        <a href="#" class="block px-3 py-2 text-xs font-semibold text-white transition-colors duration-200 transform bg-gray-900 rounded-md hover:bg-gray-700">Get Started</a>

                    </div>
                </div>
            </div>
            
      
        </div>
</template>


<script>
import heroQuery from "~/apollo/queries/hero";
export default {
  data() {
 return {
  hero: Object,

 };
},

apollo: {
  hero: {
  prefetch: true,
  query:heroQuery,

	}
  },
}
</script>