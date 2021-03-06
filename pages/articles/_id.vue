<template>
<section class="text-gray-600 body-font">
 	<div class="container w-full md:max-w-6xl mx-auto pt-20">

		<div class="w-full px-4 md:px-6 text-xl text-gray-800 leading-normal" style="font-family:Georgia,serif;">

			<!--Title-->
			<div class="font-sans">
				<p class="text-base md:text-sm text-green-500 font-bold">&lt; <a href="#" class="text-base md:text-sm text-green-500 font-bold no-underline hover:underline" @click="$router.go(-1)">BACK TO BLOG</a></p>
					
					
					<h1 class="font-bold font-sans break-normal text-gray-900 pt-6 pb-2 text-3xl md:text-4xl">{{article.Title}}</h1>
					<p class="text-sm md:text-base font-normal text-gray-600">{{article.date}}</p>
			</div>


			<!--Post Content-->


			<!--Lead Para-->
		 <img class="object-cover w-full h-64" :src="'https://blog-strapi-11.herokuapp.com' + article.thumbnail.url" alt="blog" >

			<p class="py-6">{{article.content}}</p>
			<!--/ Post Content-->

		</div>

		<!--Tags -->
		<div class="text-base md:text-sm text-gray-500 px-4 py-6">
			Tags: <a href="#" class="text-base md:text-sm text-green-500 no-underline hover:underline">Link</a> . <a href="#" class="text-base md:text-sm text-green-500 no-underline hover:underline">Link</a>
		</div>

		<!--Divider-->
		<hr class="border-b-2 border-gray-400 mb-8 mx-4">

		<!--Author-->
		<div class="flex w-full items-center font-sans px-4 py-12">
			<img class="w-20 h-20 rounded-full mr-4 object-cover object-center" :src="'https://blog-strapi-11.herokuapp.com' + article.users_permissions_user.avatar.url" alt="Avatar of Author">
			<div class="flex-1 px-2">
				<p class="text-base font-bold text-base md:text-xl leading-none mb-2 ">{{article.users_permissions_user.name}} {{article.users_permissions_user.surname}}</p>
				<p class="text-gray-600 text-xs md:text-base w-4/5">{{article.users_permissions_user.short_bio}}</p>
			</div>
			<div class="justify-end">
				
			  <router-link :to="{ name: 'users-id', params:  { id: article.users_permissions_user.id }}" tag="button" class="bg-transparent border border-gray-500 hover:border-green-500 text-xs text-gray-500 hover:text-green-500 font-bold py-2 px-4 rounded-full">		
					Read More</router-link>
			</div>
		</div>
		<!--/Author-->

		<!--Divider-->
		<hr class="border-b-2 border-gray-400 mb-8 mx-4">

		<!--comments
		<Comments/>
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

