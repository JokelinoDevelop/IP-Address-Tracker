<template>
  <div class="flex flex-col h-screen max-h-screen relative">
    <article class="absolute w-full">
      <img src="images/pattern-bg-desktop.png" alt="" class="w-full h-80 object-cover">
    </article>

    <IpAddressDash />

  </div>
</template>


<script setup>
import IpAddressDash from '@/components/IpAddressDash.vue';

</script>