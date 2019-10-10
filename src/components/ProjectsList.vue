<template>
  <div class="ProjectsList w-full md:w-2/3 md:ml-auto">
    <div class="pl-4 text-6xl text-left font-bold">Projects.</div>
    <div class="flex flex-row flex-wrap">
      <div
        v-for="repo in userRepos"
        v-bind:key="repo.id"
        class="cardWrapper m-4 rounded w-full md:w-1/2 p-4"
      >
        <div class="pb-2 text-lg text-left font-bold">{{ repo.name }}</div>
        <div class="pb-2 text-lg text-left">
          {{ repo.description || "Add repo description here!" }}
        </div>
        <div class="text-lg text-left flex">
          <div class="mr-8">
            <span class="pr-2 fas fa-code"></span>{{ repo.language }}
          </div>
          <div class="mr-8">
            <span class="pr-2 fas fa-star"></span>{{ repo.stargazers_count }}
          </div>
          <div class="mr-8">
            <span class="pr-2 fas fa-code-branch"></span>{{ repo.forks }}
          </div>
        </div>
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
  },

  data() {
    return {
      userRepos: []
    };
  },

  beforeMount() {
    fetch("https://api.github.com/users/francozeira/repos")
      .then(response => response.json())
      .then(json => {
        this.userRepos = json;
        console.log(this.userRepos);
      });
    // .catch(console.log("Something went wrong with Github API info"))
  }
};
</script>

<style>
.ProjectsList {
  background-color: black;
}

.cardWrapper {
  background-color: rgba(100, 100, 100, 0.15);
}
</style>
