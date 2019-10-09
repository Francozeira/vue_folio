<template>
  <div class="projectsSidebar test bg-teal-900 w-full md:w-1/3 h-screen">
    <div class="pt-24 ml-12">
      <div class="bg-white h-48 w-48 rounded">
        <img
          :src="userInfo.avatar_url"
          class="p-2 rounded-full"
          alt="User image"
        />
      </div>
      <div class="pt-8 text-2xl text-left font-bold">{{ userInfo.name }}</div>
      <div class="text-lg text-left font-bold">@{{ userInfo.login }}</div>
      <div class="pt-8 text-left font-bold text-sm">
        <span class="pr-1 fas fa-address-card"></span>
        {{ userInfo.bio }}
      </div>
      <div class="pt-3 text-left font-bold text-sm">
        <span class="pr-1 fas fa-map-marker-alt"></span>
        {{ userInfo.location }}
      </div>
      <div class="pt-3 text-left font-bold text-sm">
        <span class="pr-1 fas fa-briefcase"></span>
        {{ userInfo.company }}
      </div>
      <div v-if="userInfo.hireable" class="pt-3 text-left font-bold text-sm">
        <span class="pr-1 fas fa-link"></span>Hireable
      </div>
    </div>

    <div class="w-3/4 mx-auto">
      <div class="h-8 p-8 fa-2x fab fa-linkedin"></div>
      <div class="h-8 p-8 fa-2x fab fa-instagram"></div>
      <div class="h-8 p-8 fa-2x fab fa-github-square"></div>
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
/* .test {
  background-size: cover;
  background: url('https://d.newsweek.com/en/full/658174/cassini-launch.jpg?w=1600&h=1600&q=88&f=c17a0f41d7a9cbd93e1041ebbd45f181')
} */
</style>
