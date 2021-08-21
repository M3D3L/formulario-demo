<template>
  <div>
    <span class="flex">
      <div
        :class="color"
        class="text-center rounded-full w-9 h-9 b">
        <div
          :placeholder="placeholder"
          class="mt-1">
          {{ placeholder }}
        </div>
      </div>
      <hr class="w-4 mt-4 ml-1 border-dashed">
    </span>
  </div>
</template>

<script>
  export default {
    props: {
      placeholder: String,
      color: String
    },
  };
  </script>
