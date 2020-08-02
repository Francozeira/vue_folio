<template>
  <div
    class="projectsSidebar bg-black w-full absolute md:w-1/3 md:h-full md:fixed z-0 md:overflow-hidden"
  >
    <div class="pt-12 md:pt-24 md:ml-12">
      <div class="imgContainer h-48 w-48 rounded mx-auto md:mx-0">
        <img :src="userInfo.avatar_url" class="p-2" alt="User image" />
      </div>
      <div class="pt-8 text-2xl md:text-left text-center font-bold">
        <span class="description"> {{ userInfo.name }}</span>
      </div>
      <div class="text-lg md:text-left text-center font-bold">
        <span class="description"> @{{ userInfo.login }}</span>
      </div>
      <div class="pt-8 md:text-left text-center font-bold text-sm">
        <span class="pr-1 fas fa-address-card"></span> 
        <span class="description"> {{ userInfo.bio }}</span>
      </div>
      <div class="pt-3 md:text-left text-center font-bold text-sm">
        <span class="pr-1 fas fa-map-marker-alt"></span>
        <span class="description"> {{ userInfo.location }}</span>
      </div>
      <div class="pt-3 md:text-left text-center font-bold text-sm">
        <span class="pr-1 fas fa-briefcase"></span>
        <span class="description"> {{ userInfo.company }}</span>
      </div>
      <div
        v-if="userInfo.hireable"
        class="pt-3 md:text-left text-center font-bold text-sm"
      >
        <span class="pr-1 fas fa-link"></span> <span class="description"> Hireable</span>
      </div>
    </div>

    <div class="w-3/4 mx-auto">
      <a
        class="h-8 p-8 fa-2x fas fa-envelope"
        href="mailto:leofranco1305@gmail.com?Subject=Hello%20from%20Portfolio!"
      ></a>
      <a
        class="h-8 p-8 fa-2x fab fa-github-square"
        href="https://www.github.com/Francozeira"
      ></a>
      <a
        class="h-8 p-8 fa-2x fab fa-linkedin"
        href="https://www.linkedin.com/in/leo-franco-41b769169"
      ></a>
      <a
        class="h-8 p-8 fa-2x fab fa-instagram"
        href="https://www.instagram.com/francozeira"
      ></a>
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
}
</script>

<style>
.projectsSidebar {
  background-repeat: no-repeat;
  background-size: contain;
  background-position: bottom;

  background-image: url("//live.staticflickr.com/8146/29524633970_5c4b0e9074_b.jpg");
  background-image: url("//live.staticflickr.com/65535/48866057801_0e704cd2b5_k.jpg");
  background-image: url("//live.staticflickr.com/4458/37561603242_ba98acd01e_k.jpg");
  background-image: url("//live.staticflickr.com/8451/29366404680_7f463e607f_h.jpg");
  background-image: url("//live.staticflickr.com/8444/29457787572_360aff5aa3.jpg");
  /* TOP DA TOP */
  background-image: url("//live.staticflickr.com/8240/29457794852_09ccedfc3b.jpg");
  /* background-image: url('');
  background-image: url('');
  background-image: url('');
  background-image: url('');
  background-image: url('');
  background-image: url(''); */
}

.imgContainer {
  background: conic-gradient(
    hsl(100 100% 60%),
  	hsl(200 100% 60%),
  	hsl(100 100% 60%)
  );
}

.description {
  padding: 5px;
  border-radius: 5px;
  background: rgba(0, 0, 0, 0.4)
}
</style>
