<script>
    let supplyBalance = 100;
    let borrowBalance = 100;
    let netApy = 1.63;
    let borrowLimit = 192022.08;
    let currentBalance = 120000.05;
    let percentage = (currentBalance/borrowLimit)*100;
  
    let supplyMarkets = [
      { image: "", name: "Dai", apy: "4.65%", wallet: "$1000", collateral: true },
      { image:"", name: "USD Coin", apy: "-4.7%", wallet: "$190", collateral: false },
      { image: "", name: "Tether", apy: "1.08%", wallet: "$1660", collateral: true }
    ];
  
    let borrowMarkets = [
      { image: "", name: "Wrapped BTC", apy: "4.65%", wallet: "$500", limit: "20" },
      { image:"", name: "Theter", apy: "2.65%", wallet: "$6904", limit: "20" }
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
        <a href="#" class="hover:underline">Missions</a>
        <a href="#" class="hover:underline">Borrowing & Lending</a>
      </div>
      <button class="bg-yellow-500 px-4 py-2 rounded-full text-black end-full absolute right-10">Sign Up</button>
    </nav>
  

    <div class="flex ml-20 mr-20 justify-between mt-10">

      <div class=" flex flex-col items-center">
        <span class="font-semibold text-2xl m-2">Supply Balance:</span>
        <span class="font-semibold text-3xl m-4 text-green-400">${supplyBalance}</span>
        <button class="bg-yellow-500 px-4 py-2 rounded-full text-black mt-2">Supply</button>
      </div>

      <div class="w-50 h-50 rounded-full border-[10px] border-transparent flex items-center justify-center text-white text-lg font-bold relative">
        <span class="absolute flex text-center justify-center text-4xl font-bold p-10 m-10">Net APY: {netApy}%</span>
        <div class="absolute inset-0 rounded-full border-[10px] border-transparent" style="border-image: url('src/lib/assets/smallbackground.png') 30 round;">
        </div>
      </div>

      <div class="flex flex-col items-center">
        <span class="font-semibold text-2xl m-2">Borrow Balance:</span>
        <span class="font-semibold text-3xl m-4 text-red-400">${borrowBalance}</span>
        <button class="bg-yellow-500 px-4 py-2 rounded-full text-black mt-2">Borrow</button>
      </div>
     </div>
  
    <div class="w-full bg-gray-700 h-2 mt-4 relative">
      <div class="bg-green-400 h-2" style="width: {percentage}%;"></div>
      <span class="absolute left-0 text-xs text-gray-400">Current Balance: ${currentBalance}</span>
      <span class="absolute right-0 text-xs text-gray-400">${borrowLimit}</span>
    </div>
  
    <div class="grid grid-cols-2 gap-6 mt-10">
      <div class="bg-gray-800 p-6 rounded-lg opacity-80">
        <h2 class="text-xl font-bold">Supply Markets</h2>
        <div class="w-[80]% border-t border-gray-400 my-3"></div>
        <table class="w-full mt-4">
          <thead>
            <tr class="text-left">
              <th>Icon</th><th>Assets</th><th>APY</th><th>Wallet</th><th>Collateral</th>
            </tr>
          </thead>
          <tbody>
            {#each supplyMarkets as market}
              <tr>
                <td class="py-2">{market.image}</td>
                <td class="py-2">{market.name}</td>
                <td class="py-2">{market.apy}</td>
                <td class="py-2">{market.wallet}</td>
                <td class="py-2"><input type="checkbox" checked={market.collateral} class="toggle"></td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
      <div class="bg-gray-800 p-6 rounded-lg opacity-80">
        <h2 class="text-xl font-bold">Borrow Markets</h2>
        <div class="w-[80%] border-t border-gray-400 my-3"></div>
        <table class="w-full mt-4">
          <thead>
            <tr class="text-left">
              <th>Icon</th><th>Assets</th><th>APY</th><th>Wallet</th><th>% of Limit</th>
            </tr>
          </thead>
          <tbody>
            {#each borrowMarkets as market}
              <tr>
                <td class="py-2">{market.image}</td>
                <td class="py-2">{market.name}</td>
                <td class="py-2">{market.apy}</td>
                <td class="py-2">{market.wallet}</td>
                <td class="py-2"><div class="bg-red-400 h-2" style="width:{market.limit}%"></div></td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
    </div>
  </div>

  
  
  
  