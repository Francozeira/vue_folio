<template>
  <div class="ProjectsList w-full md:w-2/3 md:ml-auto">
    <div id="nav" class="text-2xl text-right">
      <!-- <router-link to="/"><span class="pr-2 fas fa-home fa-3x"></span></router-link>  -->

      <router-link to="/">Home</router-link>|
      <router-link to="/projects">Projects</router-link>
    </div>
    <div class="pl-4 mb-12 text-6xl text-left font-bold">Projects.</div>
    <div v-if="!infoLoaded" class="background-teal-400">ONLY THIS</div>
    <div v-if="infoLoaded">
      <div class="flex flex-row flex-wrap">
        <div
          v-for="(repo, i) in userRepos"
          v-bind:key="repo.id"
          class="w-full md:w-1/2"
        >
          <div
            class="cardWrapper rounded p-4 mb-4 ml-4"
            v-bind:class="{ 'mr-4': i % 2 == 1 }"
          >
            <div class="pb-2 text-lg text-left font-bold">{{ repo.name }}</div>
            <div class="pb-2 text-lg text-left">
              {{ repo.description || "Insert description here!" }}
            </div>
            <div class="pb-2 text-lg text-left text-teal-400">
              {{ parsedDescription[i] }}
            </div>
            <div class="text-lg text-left flex">
              <div class="mr-8">
                <span class="pr-2 fas fa-code"></span>
                {{ repo.language }}
              </div>
              <div class="mr-8">
                <span class="pr-2 fas fa-star"></span>
                {{ repo.stargazers_count }}
              </div>
              <div class="mr-8">
                <span class="pr-2 fas fa-code-branch"></span>
                {{ repo.forks }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="my-12 text-lg text-center">
      Vue.JS implementation of @imfunniee/<a
        id="imfunnieeLink"
        href="https://github.com/imfunniee/gitfolio"
        >gitfolio</a
      >
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
      infoLoaded: false,
      userRepos: [],
      parsedDescription: ["Add repo description here!"]
    };
  },

  beforeMount() {
    fetch("https://api.github.com/users/francozeira/repos")
      .then(response => response.json())
      .then(json => {
        this.userRepos = json;
        // console.log(this.userRepos);
        this.infoLoaded = true;
      });
    // .catch(console.log("Something went wrong with Github API info"))
  },

  methods: {
    descriptionParser(data) {
      // let dscrt = data;
      // console.log(dscrt.split(/\b\\\:*\:\b/));

      return data;
    },

    parse() {
      //   console.log(this.userRepos[0].description);
    }
  },

  // computed: {
  //   description: function () {
  //     return userRepos[0].description
  //   }
  // },

  watch: {
    infoLoaded: function() {
      for (let i = 0; i < this.userRepos.length; i++) {
        this.userRepos[i].description === null ?
          this.parsedDescription[i] = "No repo description avaliable"
          : this.parsedDescription[i] = this.userRepos[i].description.match(/\:[^\W]*\:/g);
      }
          console.log(this.parsedDescription);

    }


  }
};

// :sweat_smile: :mortar_board: small, ugly and simple portfolio for developing skills

</script>

<style>
.ProjectsList {
  background-color: black;
}

.cardWrapper {
  background-color: rgba(100, 100, 100, 0.15);
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: white;
}

#nav a.router-link-exact-active,
#imfunnieeLink {
  color: #139786;
}
</style>
