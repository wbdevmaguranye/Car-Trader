<template>
     <!-- CAR SIDE BAR -->
     <div class="shadow border w-64 mr-10 z-30 h-[190px]">
      <div class="p-5 flex justify-between relative cursor-pointer border-b">
      <h3>Location</h3>
      <h3 class="text-blue-400 capitalize ml-2" @click="updateModal('location')">{{route.params.city}}</h3>
      <div class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white" v-if="modal.location">
      <input type="text" class="border p-1 rounded" v-model="city" />
      <button class="bg-blue-400 w-full mt-2 rounded text-white p-1" @click="onChangeLocation">Apply</button>
      </div>
      </div>
      <div class="p-5 flex justify-between relative cursor-pointer border-b">
        <h3>Make</h3>
      <h3 class="text-blue-400 capitalize">Toyota</h3>
      </div>
      <div class="p-5 flex justify-between relative cursor-pointer border-b">
        <h3>Price</h3>
      <h3 class="text-blue-400 capitalize">$$</h3>
      </div>
      </div>
      <!-- CAR SIDE BAR -->
</template>
<script setup>
const modal = ref({
  make:false,
  location:false,
  price:false
});
const city = ref("")
const route = useRoute();

const updateModal = (key) =>{ 
modal.value[key] = !modal.value[key] 
};

const onChangeLocation = () => {
  if(!city.value) return;
  if(!isNaN(parseInt(city.value))){
    throw createError({
      statusCode:400,
      message:"Invalid city formmat"
    })
  }
  updateModal("location");
  navigateTo(`/city/${city.value}/car/${route.params.make}`);
  city.value="";
}
</script>