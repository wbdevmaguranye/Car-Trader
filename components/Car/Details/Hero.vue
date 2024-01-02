<template>
       <!-- CAR HERO -->
       <div class="mt-10">
          <NuxtImg
            :src="car.url"
            alt=""
            class="w-full"
          />
          <h1 class="mt-10 text-4xl">{{car.name}}</h1>
          <div
            class="text-slate-500 flex text-lg mt-3 border-b justify-between"
          >
            <div class="flex">
              <p class="mr-2">{{car.seats}}</p>
              <p class="mr-2">|</p>
              <p class="mr-2">{{ car.miles }}</p>
            </div>
            <div>
              <p class="font-bold text-2xl">{{car.price}}</p> 
            </div>
          </div>
        </div>
        <!-- CAR HERO -->
</template>
<script setup>
const props = defineProps({
  car:Object
})
</script>