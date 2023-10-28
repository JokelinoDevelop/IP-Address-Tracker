<template>
  <article
    class="z-20 lg:top-48 top-36 px-4 py-8 absolute left-1/2 transform -translate-x-1/2 max-w-screen-lg  bg-white shadow-md rounded-xl text-center lg:text-left ">
    <ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 md:px-4  gap-x-4 gap-y-2 lg:px-8 w-full">

      <!-- flex flex-col lg:flex-row -->

      <li class="lg:border-r-2 lg:pr-4 lg:border-slate-200">
        <p class="text-sm md:text-lg font-[700] text-darkGray mb-1">IP ADDRESS</p>
        <h2 class="text-xl md:text-2xl font-[500]">{{ ipInfo.address }}</h2>
      </li>

      <li class="lg:border-r-2 lg:pr-4 lg:border-slate-200">
        <p class="text-sm md:text-lg font-[700] text-darkGray mb-1">LOCATION</p>
        <h2 class="text-xl md:text-2xl font-[500]">{{ ipInfo.location }}</h2>
      </li>

      <li class="lg:border-r-2 lg:pr-4 lg:border-slate-200">
        <p class="text-sm md:text-lg font-[700] text-darkGray mb-1">TIMEZONE</p>
        <h2 class="text-xl md:text-2xl font-[500]">UTC {{ ipInfo.timezone }}</h2>
      </li>

      <li class="lg:pr-4">
        <p class="text-sm md:text-lg font-[700] text-darkGray mb-1">ISP</p>
        <h2 class="text-xl md:text-2xl font-[500]">{{ ipInfo.isp }}</h2>
      </li>

    </ul>
  </article>
</template>

<script setup>

defineProps({
  ipInfo: {
    required: true,
    type: Object
  }
})

</script>
