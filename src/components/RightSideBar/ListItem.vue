<template>
    <div class="bg-dapp-black-2 py-3 px-6 sm:px-9 md:px-10 pl-10 pr-10 flex items-center hover:bg-black justify-between cursor-pointer text-white border-b border-b-dapp-white-10 gap-2">
      <div class="w-fit flex items-center gap-1">
        <span class="w-4">
          <!-- <Icon fontSize="1rem" icon="logos:bitcoin" /> -->
          <img :src="iconUrl" />
        </span>
        <h5 class="font-normal text-white text-base 2xl:text-lg leading-[120%]">
          {{name}}
        </h5>
      </div>
      <p class="text-sm font-normal uppercase">
        Bitcoin all time history index
      </p>
      <div class="flex items-center gap-2">
        <span class="text-xs text-gray-500">spot crypto</span>
        <div class="w-fit flex items-center gap-1">
          <h5 class="font-normal text-white text-base 2xl:text-lg leading-[120%] uppercase">
            Index
          </h5>
          <span class="w-4">
            <img :src="iconUrl" />
            <!-- <Icon fontSize="1rem" icon="logos:bitcoin" /> -->
          </span>
        </div>
      </div>
      <div class="text-white hover:text-dapp-blue">
        <Icon icon="ic:sharp-plus" fontSize={24} />
      </div>
    </div>
  </template>
  
  <script>
  import { Icon } from "@iconify/vue2"; // Adjust the path as needed
  
  export default {
    components: {
      Icon,
    },
    props: {
      name: String,
      iconUrl: String
    }
  };
  </script>
  
  <style scoped>
  /* ... Other styles ... */
  </style>
  