<template>
  <div class="projects flex">
    <ProjectsSidebar :userInfo="userInfo" />
    <ProjectsList :userInfo="userInfo" />
  </div>
</template>

<script>
import ProjectsSidebar from "@/components/ProjectsSidebar.vue";
import ProjectsList from "@/components/ProjectsList.vue";

export default {
  components: {
    ProjectsSidebar,
    ProjectsList
  },

  data() {
    return {
      userInfo: []
    };
  },

  beforeMount() {
    fetch("https://api.github.com/users/francozeira")
      .then(response => response.json())
      .then(json => {
        this.userInfo = json;
        console.log(this.userInfo);
      });
    // .catch(console.log("Something went wrong with Github API info"))
  }
};
</script>

<style>
.projects {
  font-family: "Poppins", sans-serif;
  color: white;
}
</style>
