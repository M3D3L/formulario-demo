<template>
  <section class="relative ">
  <div class="mx-auto border-b border-white outline">
    <input
        :type="type"
        :placeholder="placeholder"
        class="relative z-20 block w-full text-white placeholder-white bg-transparent appearance-none md:mb-4 text-md md:text-md focus:outline-none focus:placeholder-transparent" />
    <label class="absolute top-0 z-10 text-white duration-300 text-md origin-0">
      {{ placeholder }}
    </label>
  </div>
  </section>
</template>

  <script>
  export default {
    props: [  "placeholder", "type",],
  };
  </script>

<style>

.outline input:not(:placeholder-shown) ~ label {
@apply transform scale-75 -translate-y-4 z-0 ml-3 px-1 py-0;
}


</style>
