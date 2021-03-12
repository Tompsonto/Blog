<template>
<section class="text-gray-600 body-font">
<div class=" md:flex w-screen bg-no-repeat bg-cover bg-center " style="height:60vh;"  v-bind:style="{ 'background-image': 'url(http://localhost:1337'+ article.thumbnail.url + ')' }">
        <div class="w-screen  bg-black absolute z-0 opacity-50" style="height:60vh"></div>
          
            <div class="container w-full md:max-w-6xl px-4 mx-auto pt-20 md:py-3 md:flex md:justify-between md:items-center relative">
                <div class="max-w-xl">
                    <h1 class="text-6xl font-semibold text-white dark:text-white">{{article.Title}}</h1>
                   <p class="text-sm md:text-base font-normal text-white">{{article.date|truncate(10)}}</p>
				   	<div class="font-sans">
				<p class="text-base md:text-sm text-green-500 font-bold">&lt; <a href="#" class="text-base md:text-sm text-green-500 font-bold no-underline hover:underline" @click="$router.go(-1)">BACK TO BLOG</a></p>
					
			</div>

                </div>
            </div>
            
      
        </div>
 	<div class="container w-full md:max-w-6xl mx-auto relative z-100  bg-white " style="margin-top:-3rem;">

		<div class="w-full px-4 md:px-6 text-xl text-gray-800 leading-normal" style="font-family:Georgia,serif;">

			<!--Post Content-->


			<!--Lead Para-->

			<p class="py-6">{{article.content}}</p>
			<!--/ Post Content-->

		</div>

		<!--Tags 
		<div class="text-base md:text-sm text-gray-500 px-4 py-6">
			Tags: <a href="#" class="text-base md:text-sm text-green-500 no-underline hover:underline">Link</a> . <a href="#" class="text-base md:text-sm text-green-500 no-underline hover:underline">Link</a>
		</div>-->

		<!--Divider-->
		<hr class="border-b-2 border-gray-400 mb-8 mx-4">

		<div class="flex w-full items-center font-sans px-4 pb-10">
			<img class="w-20 h-20 rounded-full mr-4 object-cover object-center" :src="'http://localhost:1337' + article.users_permissions_user.avatar.url" alt="Avatar of Author">
			<div class="flex-1 px-2">
				<p class="text-base font-bold text-base md:text-xl leading-none mb-2 ">{{article.users_permissions_user.name}} {{article.users_permissions_user.surname}}</p>
				<p class="text-gray-600 text-xs md:text-base w-4/5">{{article.users_permissions_user.short_bio}}</p>
			</div>
			<div class="justify-end">
				
			  <NuxtLink  :to="{ name: 'users-id', params:  { id: article.users_permissions_user.id }}" tag="button" class="bg-transparent border border-gray-500 hover:border-green-500 text-xs text-gray-500 hover:text-green-500 font-bold py-2 px-4 rounded-full">		
					Read More</NuxtLink>
			</div>
		</div>
		<!--/Author-->

		<!--Divider-->
		<hr class="border-b-2 border-gray-400 mb-8 mx-4">

		<!--comments
		    <div class=" md:flex container mx-auto mt-10" style="height:45vh;">
            <h2>Comments</h2>
            <div class="flex w-full items-center font-sans px-4 py-12" >
			   <ul>
				<li class="flex-1 px-2" v-for="commentry in article.comments" :key="commentry.index">
				    <p class="text-base font-bold text-base md:text-xl leading-none mb-2 ">{{commentry.nick}}</p>
				    <p class="text-gray-600 text-xs md:text-base w-4/5">{{commentry.content}}</p>
			    </li>
			   </ul>
		
		    </div>
        </div>
		<hr class="border-b-2 border-gray-400 mb-8 mx-4">-->

		<!--Next & Prev Links-->
		<div class="font-sans flex justify-between content-center px-4 pb-12">
			<div class="text-left">
				<span class="text-xs md:text-sm font-normal text-gray-600">&lt; Previous Post</span><br>
				<p><a href="#" class="break-normal text-base md:text-sm text-green-500 font-bold no-underline hover:underline">Blog title</a></p>
			</div>
			<div class="text-right">
				<span class="text-xs md:text-sm font-normal text-gray-600">Next Post &gt;</span><br>
				<p><a href="#" class="break-normal text-base md:text-sm text-green-500 font-bold no-underline hover:underline">Blog title</a></p>
			</div>
		</div>


		<!--/Next & Prev Links-->

	</div>
</section>
</template>

<script>
import articleQuery from "~/apollo/queries/article";
export default {
  data() {
 return {
  article: Object,

 };
},
  filters:{
    truncate: function(value) {
        value = value.substring(0, 10);
        return value
    }
  },
apollo: {
  article: {
  prefetch: true,
  query: articleQuery,
  variables () {
    return {
		 id: this.$route.params.id,

		}
	}
	}
  },
}
</script>

