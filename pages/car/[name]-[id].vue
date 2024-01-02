<template>
  <div v-if="car">
    <!-- {{ car }} -->
    <CarDetailsHero :car="car" />

    <CarDetailsAttributes :features="car.features"/>

    <CarDetailsDescription :description="car.description"/>

    <CarDetailsContact />

    <!-- CAR DETAIL PAGE -->
  </div>
</template>
<script setup>
const route = useRoute();
const {cars} = useCars();
useHead({
  title: route.params.name,
});
const car = computed( () =>{
return cars.find((c) =>{
  return c.id === parseInt(route.params.id);
})
});
if(!car.value){
  throw createError({
    statusCode:404,
    message: `Car with ID of ${route.params.id} does not exist`
  })
}
definePageMeta({
  layout: "custom",
});
</script>
 