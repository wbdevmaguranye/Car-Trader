<template>
  <div>
    <!-- CAR SEARCH BAR -->
    <div
      class="font-serif w-[1000px] text-2xl rounded-full bg-white flex justify-between overflow-hidden drop-shadow-2xl mx-auto"
    >
      <input
        type="text"
        class="py-3 px-5 w-full text-3xl rounded-full focus:outline-non"
        :class="cityError ? 'border-red-400 border' : ''"
        placeholder="Search by city...."
         v-model="city"
      />
      <button class="bg-sky-500 px-10 text-white" @click="handleSearch">Search</button>
    </div>
    <!-- CAR SEARCH BAR -->
  </div>
</template>
<script setup lang="ts">
const city = ref("");
const cityError = ref(false)
// const router = useRouter();
// Note that the useRouter() composable approach is a bit long , so to replace this nuxt uses the navigateTo() instead
const handleSearch = () =>{
    // router.push(`/city/${city.value}/car`);
    if(!city.value){
        return cityError.value=true
    }
    navigateTo(`/city/${city.value}/car`);
};
</script>
