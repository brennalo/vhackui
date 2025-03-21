<!-- <img src={'$lib/assets/background.png'} alt='this is a picture'>

<div class="h-full image={'background.png'}">
    <nav class="p-4 bg-purple-200 shadow md:flex md:items-center md:justify-between">
        <div class="flex-justify-between items-center place=self-center">
            <span class="text-2xl fonts-[Poppins] cursor-pointer">
                WellPlated
            </span>
        </div>
        <ul class="flex flex-row md:flex md:items-center z-[-1] md:z-auto md:static-absolute w-full items-center justify-between">
            <li class="mx-4 my-6 md:my-0">
                <a class="hover:text-gray-400 text-xl p-2" href = "/manageMenu">Manage</a> 
            </li>
            <li class="mx-4 my-6 md:my-0">
                <a class= "bg-black text-white text-xl rounded-lg p-3" href = "/#">Add</a> 
            </li>
        </ul>
    </nav>
</div> -->

<script>
  let missions = [
    { text: "Own 5 different coins at the same time" },
    { text: "Lend minimum 500USDT in total" },
    { text: "Connect to Gmail account" },
    { text: "Provide name and identification number" },
  ];

</script>


<div class="relative bg-black text-white min-h-screen p-6 -z-10">
  <video autoplay loop muted playsinline class="absolute top-0 left-0 w-full h-full object-cover opacity-50 -z-5">
    <source src="src/lib/assets/background.mp4" type="video/mp4"/>
  </video>
  <nav class="flex justify-center items-center text-lg">
    <div class="flex gap-10">
      <a href="#" class="hover:underline">Home</a>
      <a href="#" class="hover:underline">Profile</a>
      <a href="#" class="hover:underline">Missions</a>
      <a href="#" class="hover:underline">Borrowing & Lending</a>
    </div>
    <button class="bg-yellow-500 px-4 py-2 rounded text-black end-full absolute right-10">Sign Up</button>
  </nav>

  <h1 class="text-center text-4xl font-bold mt-8">Missions</h1>

  <div class="bg-gray-800 p-4 mt-6 mr-20 ml-20 rounded-lg relative shadow-yellow-400/50 shadow-2xl">
    <span class="text-yellow-400 font-bold">&#x1F4F0; Daily News</span>
    <p class="m-2 text-center text-xl font-semibold">ByBit Hack: Unveiling the $1.5 Billion Heist Linked to North Korean Hackers</p>
    <span class="absolute right-4 top-4 text-yellow-400">&rarr;</span>
  </div>

  <div class="grid grid-cols-2 gap-6 mt-10 max-w-3xl mx-auto">
    {#each missions as mission}
      <div class="bg-gray-700 p-6 rounded-lg flex items-center justify-between shadow-yellow-400/50 shadow-2xl">
        <div class="flex items-center gap-4">
          <div class="bg-yellow-500 w-10 h-10 rounded-full"></div>
          <span class="text-lg">{mission.text}</span>
        </div>
        <span class="text-yellow-400">&rarr;</span>
      </div>
    {/each}
  </div>
</div>

<div class="custom-shape"></div>

<style>
  .custom-shape {
    width: 300px;
    height: 80px;
    background: lightgray;
    border: 2px solid black;
    clip-path: polygon(0 0, 100% 0, 100% 70%, 85% 100%, 0 100%);
    position: relative;
  }
</style>




