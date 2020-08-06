<template>
  <div class="projects flex">
    <ProjectsSidebar :userInfo="userInfo" />
    <ProjectsList :userInfo="userInfo" />
  </div>
</template>

<script>
import ProjectsSidebar from '@/components/ProjectsSidebar.vue'
import ProjectsList from '@/components/ProjectsList.vue'

export default {
	components: {
		ProjectsSidebar,
		ProjectsList
	},

	data() {
		return {
			userURL: 'https://api.github.com/users/francozeira',
			userInfo: []
		}
	},

	beforeMount() {
		fetch(this.userURL)
			.then(response => response.json())
			.then(json => {
				this.userInfo = json
				console.log(this.userInfo)
			})
			// .catch(console.log('Something went wrong with Github API info'))
	}
}
</script>

<style>
.projects {
  font-family: "Poppins", sans-serif;
  color: white;
}

/* width */
::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  background: black;
}
 
/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(255, 255, 255); 
  border-radius: 10px;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #4fd1c5; 
}
</style>
