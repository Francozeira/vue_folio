<template>
  <div
    class="ProjectsList h-full w-full pt-64 mt-64 md:p-0 md:m-0 md:w-2/3 md:ml-auto"
  >
    <div class="pt-8 md:p-0 pl-4 mb-12 text-6xl text-left font-bold">Projects.</div>
    <div v-if="!infoLoaded" class="background-teal-400">LOADING...</div>
    <div v-if="infoLoaded">
      <div class="flex flex-row flex-wrap">
        <div
          v-for="(repo, i) in userRepos"
          v-bind:key="repo.id"
          class="w-full md:w-1/2"
          @click="selectRepo(repo.html_url)"
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
              <i class="fas fa-cross"></i>
              {{ formatedDate(repo.created_at) }}
                <span class="text-white separator"> |   </span>  
              <i class="fas fa-edit"></i>
              {{ formatedDate(repo.updated_at) }}
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
      Vue.JS implementation based on @imfunniee/<a
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
			required: true,
		},
	},

	data() {
		return {
			infoLoaded: false,
			userRepos: [],
			parsedDescription: ['Add repo description here!'],
		}
	},

	beforeMount() {
		fetch('https://api.github.com/users/francozeira/repos')
			.then((response) => response.json())
			.then((json) => {
				this.userRepos = json
				this.infoLoaded = true
			})
	},

	methods: {
		selectRepo: function (repo) {
			window.open(repo, '_blank')
		},
		formatedDate: unparsedDate => {
			const date = new Date(unparsedDate)
			const dd = String(date. getDate()). padStart(2, '0')
			const mm = String(date. getMonth() + 1). padStart(2, '0')
			const yyyy = date. getFullYear()
			return dd + '/' + mm + '/' + yyyy  
		},
	},

	watch: {
		infoLoaded: function() {
      
			this.userRepos.forEach( (repo,i) => {
				repo.description === null
					? (this.parsedDescription[i] = 'No repo description avaliable')
					: (this.parsedDescription[i] = this.userRepos[i].description.match(
						/\:[a-z,0-9,_,+,-]+\:/g))
			})
			console.log(this.parsedDescription)
		},
	},
}
</script>

<style>
.ProjectsList {
  background-color: black;
  overflow-x: hidden;
}

.cardWrapper {
  background-color: rgba(100, 100, 100, 0.15);
  cursor: pointer;
  transition: 3s;
}

.cardWrapper:hover {
  transform: scale(1.1);
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
  transition: 2s;
}

#imfunnieeLink:hover {
  color: #1feed2;
  font-size: 1.2em;
}

.separator {
  white-space:pre;
}

/* MEDIA QUERIES */
@media only screen and (max-width: 767px) {
  .cardWrapper {
    margin-right: 1rem;
  }
}
</style>