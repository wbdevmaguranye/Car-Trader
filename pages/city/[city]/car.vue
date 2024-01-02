<template>
  <div>
    <div
      class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5"
    >
      <div class="mt-32 flex">
        <NuxtErrorBoundary>
          <CarSideBar />
          <NuxtPage />
          <template #error="{error}">
<div class="text-center mx-auto flex flex-col">
<h1 class=" text-5xl text-red-500 mb-4">Sorry, something went wrong</h1>
<code>{{ error }}</code>
<button class="text-white bg-blue-400 px-10 py-3 rounded mt-4" @click="error.value =null">Go back</button>
</div>

          </template>
        </NuxtErrorBoundary>
      </div>
    </div>
  </div>
</template>
<script setup>
const route = useRoute();
useHead({
  title: `${
    route.params.make ? toUpperCase(route.params.make) : "Cars"
  } in ${route.params.city.toUpperCase()}`,
});
</script>
