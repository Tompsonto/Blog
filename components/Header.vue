<template>
<header class=" body-font z-50	 absolute w-screen" :class="{'text-black':dark, 'text-white':!dark}">
   <nav class=" dark:bg-gray-50 relative">
        <div class="container px-6 py-3 mx-auto md:flex md:justify-between md:items-center relative">
            <div class="flex items-center justify-between relative">
                <div>
                   
                     <NuxtLink to="/" tag="a" :class="{'text-black':dark, 'text-white':!dark}" class="text-xl font-bold  dark:text-white md:text-2xl hover:text-gray-700 dark:hover:text-gray-300">Blog</NuxtLink>
                </div>
                
                <!-- Mobile menu button -->
                <div class="flex md:hidden" @click="isActive = !isActive">
                    <button type="button" :class="{'text-black':dark, 'text-white':!dark}" class=" dark:text-gray-200 hover:text-gray-800 dark:hover:text-gray-400 focus:outline-none focus:text-gray-600 dark:focus:text-gray-400" aria-label="toggle menu">
                        <svg viewBox="0 0 24 24" class="w-6 h-6 fill-current">
                            <path fill-rule="evenodd" d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"></path>
                        </svg>
                    </button>
                </div>
            </div>

            <!-- Mobile Menu open: "block", Menu closed: "hidden" -->
            <div class="bg-gray-800 items-center md:flex md:bg-transparent  " :class="{block:isActive, hidden:!isActive}">
                <div class="flex flex-col md:flex-row md:mx-6">
                    <a :class="{'text-black':dark, 'text-white':!dark}" class="my-1 text-sm font-medium  dark:text-gray-200 hover:text-indigo-500 dark:hover:text-indigo-400 md:mx-4 md:my-0" href="#">Blog</a>
                    <a :class="{'text-black':dark, 'text-white':!dark}" class="my-1 text-sm font-medium  dark:text-gray-200 hover:text-indigo-500 dark:hover:text-indigo-400 md:mx-4 md:my-0" href="#">costam</a>

  <NuxtLink :to="{ name: 'about'}" tag="a" :class="{'text-black':dark, 'text-white':!dark}" class="my-1 text-sm font-medium  dark:text-gray-200 hover:text-indigo-500 dark:hover:text-indigo-400 md:mx-4 md:my-0">About</NuxtLink>
                </div>

            </div>
        </div>
    </nav>
</header>
</template>


<script>

export default {
  data() {
    return {
    isActive: false,
    id: this.$route.fullPath,
    dark:false
    }
  },
mounted(){
    
         this.dark = this.id.includes("users")
    
   
}


}
</script>

