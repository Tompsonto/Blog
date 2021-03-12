<template>
  <div class=" md:flex w-screen bg-no-repeat bg-cover bg-center " style="height:60vh;"  v-bind:style="{ 'background-image': 'url(http://localhost:1337'+ articleHero.thumbnail.url + ')' }">
    <div class="w-screen  bg-black absolute z-0 opacity-50" style="height:60vh"></div>
        
    <div class="container w-full md:max-w-6xl px-4 mx-auto pt-20 md:py-3 md:flex md:justify-between md:items-center relative">
      <div class="max-w-xl pt-18">
        <h1 class="text-6xl font-semibold text-white dark:text-white">{{articleHero.Title}}</h1>
        <p class="text-sm md:text-base font-normal text-white">{{articleHero.date|truncate(10)}}</p>

				<div class="font-sans">
				  <p class="text-base md:text-sm text-green-500 font-bold">&lt; <a href="#" class="text-base md:text-sm text-green-500 font-bold no-underline hover:underline" @click="$router.go(-1)">BACK TO BLOG</a></p>
			  </div>

      </div>
    </div>
  
  </div>
</template>


<script>
import articleHeroQuery from "~/apollo/queries/articleHero";
export default {
  data() {
 return {
  articleHero: Object,

 };
},

apollo: {
  articleHero: {
    prefetch: true,
    query:articleHeroQuery,
	  }
  },
}
</script>