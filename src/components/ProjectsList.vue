<template>
  <div class="ProjectsList flex w-full md:w-2/3">
    <div class="cardWrapper bg-gray-900 m-4 rounded w-full md:w-1/2 h-40">
      <div class="p-4 text-lg text-left">RHCP</div>
      <div class="px-4 text-lg text-left">desciption of the repo.</div>
      <div class="px-4 text-lg text-left flex">
        <div class="mr-4"><span class="pr-1 fas fa-code"></span>Vue</div>
        <div class="mr-4"><span class="pr-1 fas fa-star"></span>99</div>
        <div class="mr-4"><span class="pr-1 fas fa-code-branch"></span>6</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    userInfo: {
      required: true
    }
  }
};
</script>

<style>
.ProjectsList {
  background-color: black;
  /* background: url('https://d.newsweek.com/en/full/658174/cassini-launch.jpg?w=1600&h=1600&q=88&f=c17a0f41d7a9cbd93e1041ebbd45f181') */
}
</style>
