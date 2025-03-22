
<script>
  let missions = [
    { text: "Own 5 different coins at the same time" },
    { text: "Lend minimum 500USDT in total" },
    { text: "Connect to Gmail account" },
    { text: "Provide name and identification number" },
  ];

</script>


<div class="relative bg-black text-white min-h-screen p-6 -z-10">
  <video autoplay loop muted playsinline class="fixed top-0 left-0 w-full h-full object-cover opacity-50 -z-5 ">
    <source src="src/lib/assets/background.mp4" type="video/mp4">
  </video>
  <nav class="flex justify-center items-center text-lg">
    <div class="flex gap-10">
      <a href="#" class="hover:underline">Home</a>
      <a href="#" class="hover:underline">Profile</a>
      <a href="/#" class="hover:underline">Missions</a>
      <a href="/borrowing" class="hover:underline">Borrowing & Lending</a>
    </div>
    <button class="bg-yellow-500 px-4 py-2 rounded-full text-black end-full absolute right-10">Sign Up</button>
  </nav>

  <h1 class="text-center text-4xl font-bold mt-8">Missions</h1>

  <div class="bg-gray-800 p-4 mt-6 mr-20 ml-20 rounded-lg relative shadow-yellow-400/50 shadow-2xl bg-cover" style = "background-image:url('src/lib/assets/try.png')">
    <span class="text-yellow-400 font-bold">&#x1F4F0; Daily News</span>
    <p class="m-2 text-center text-2xl font-bold">ByBit Hack: Unveiling the $1.5 Billion Heist Linked to North Korean Hackers</p>
    <span class="absolute right-4 top-4 text-yellow-400">&rarr;</span>
  </div>

  <div class="grid grid-cols-2 gap-10 mt-5 max-w-3xl mx-auto">
    {#each missions as mission}
    <div class="relative">
    <div class="diamond absolute left-1/2 top-6 z-2 transform -translate-x-1/2 w-12 h-12 bg-center bg-cover" 
    style="background-image:url('src/lib/assets/smallbackground.png')"></div>
      <div class="custom-shape bg-gray-500 p-4 m-4 flex items-center justify-between shadow-white shadow-xl opacity-80">
          <span class="text-lg font-semibold text-yellow-200 text-shadow">{mission.text}</span>
        <span class="text-yellow-400">&rarr;</span>
      </div>
      </div>
    {/each}
  </div>
</div>


<style>
  .custom-shape {
    width: 350px;
    height: 120px;
    clip-path: polygon(0 0, 100% 0, 100% 70%, 70% 70%, 60% 100%,0% 100%);
    position: relative;
  }

  .custom-shape::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgb(15, 15, 90);
    clip-path: polygon(0 0, 100% 0, 100% 70%, 70% 70%, 60% 100%,0% 100%);
    z-index: -1;
    right: 3px;
    bottom: 3px;
    opacity: 0.5;
    }

  .diamond{
    width: 100px;
    height: 100px;
    background:rgb(165, 120, 81);
    clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
    position: relative;
  }
</style>





