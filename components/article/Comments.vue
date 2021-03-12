<template>
		<div class=" md:flex container mx-auto mt-10" style="height:45vh;">
            
            <div class="flex w-full items-center font-sans px-4 py-12" >
			   <ul>
				<li class="flex-1 px-2" v-for="commentry in article.comments" :key="commentry.index">
				    <p class="text-base font-bold text-base md:text-xl leading-none mb-2 ">{{commentry.nick}}</p>
				    <p class="text-gray-600 text-xs md:text-base w-4/5">{{commentry.content}}</p>
			    </li>
			   </ul>
		
		    </div>
        </div>
</template>


<script>
import ArticleComments from "~/apollo/queries/articleComments";
export default {
  data() {
 return {
  comments: Object,

 };
},

apollo: {
  comments: {
  prefetch: true,
  query:ArticleComments,
	}
},
}
</script>