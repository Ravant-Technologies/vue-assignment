<template>
    <span
      class="py-1 px-3 ml-5 mt-2 text-sm text-white rounded-full inline-block cursor-pointer"
      :class="{
        'hover:bg-dapp-blue': !active,
        'bg-dapp-blue': active,
        'bg-dapp-black-5': !active,
      }"
      @click="handleClick"
    >
      <slot></slot>
    </span>
  </template>
  
  <script>
  export default {
    props: {
      active: Boolean,
    },
    methods: {
      handleClick() {
        this.$emit("onClick");
      },
    },
  };
  </script>
  
  <style scoped>
  /* ... Other styles ... */
  </style>
  