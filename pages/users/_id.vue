<template>
<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto flex flex-col">
    <div class="lg:w-4/6 mx-auto">
      <div class="flex flex-col sm:flex-row mt-10">
        <div class="sm:w-1/3 text-center sm:pr-8 sm:py-8">
         
          <img class="object-cover h-50  inline-flex items-center justify-center" :src="'http://localhost:1337' + user.avatar.url" alt="blog" >
         
          <div class="flex flex-col items-center text-center justify-center">
            <h2 class="font-medium title-font mt-4 text-gray-900 text-lg">{{user.name}} {{user.surname}}</h2>
         
          </div>
        </div>
        <div class="sm:w-2/3 sm:pl-8 sm:py-8 sm:border-l border-gray-200 sm:border-t-0 border-t mt-4 pt-4 sm:mt-0 text-center sm:text-left">
          <p class="leading-relaxed text-lg mb-4">{{user.bio}}</p>
       
        </div>
      </div>
    </div>
  </div>
</section>
</template>

<script>
import userQuery from "~/apollo/queries/user";
export default {
  data() {
 return {
  user: Object,

 };
},
apollo: {
  user: {
  prefetch: true,
  query: userQuery,
  variables () {
    return {
		 id: this.$route.params.id,

		}
	}
	}
  },
}
</script>

