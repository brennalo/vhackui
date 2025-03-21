<script>
    let supplyBalance = 100;
    let borrowBalance = 100;
    let netApy = 1.63;
    let borrowLimit = 192022.08;
  
    let supplyMarkets = [
      { name: "Dai", apy: "4.65%", wallet: "$1000", collateral: true },
      { name: "USD Coin", apy: "-4.7%", wallet: "$190", collateral: false },
      { name: "Tether", apy: "1.08%", wallet: "$1660", collateral: true }
    ];
  
    let borrowMarkets = [
      { name: "Wrapped BTC", apy: "4.65%", wallet: "$500", limit: "20%" },
      { name: "Theter", apy: "2.65%", wallet: "$6904", limit: "20%" }
    ];
  </script>
  
  <div class="relative bg-black text-white min-h-screen p-6">
    <video autoplay loop muted playsinline class="absolute top-0 left-0 w-full h-full object-cover opacity-50">
        <source src="src/lib/assets/background.mp4" type="video/mp4"/>
      </video>
    <nav class="flex justify-between items-center text-lg">
      <div class="flex gap-4">
        <a href="#" class="hover:underline">Home</a>
        <a href="#" class="hover:underline">Profile</a>
        <a href="#" class="hover:underline">Missions</a>
        <a href="#" class="hover:underline">Borrowing & Lending</a>
      </div>
      <button class="bg-yellow-500 px-4 py-2 rounded text-black">Sign Up</button>
    </nav>
  
    <div class="flex justify-center mt-10 text-4xl font-bold">Net APY: {netApy}%</div>
  
    <div class="flex justify-between mt-10">
      <div class="text-green-400">Supply Balance: ${supplyBalance} <button class="bg-yellow-500 px-4 py-2 rounded text-black ml-4">Lend</button></div>
      <div class="text-red-400">Borrow Balance: ${borrowBalance} <button class="bg-yellow-500 px-4 py-2 rounded text-black ml-4">Borrow</button></div>
    </div>
  
    <div class="w-full bg-gray-700 h-2 mt-4 relative">
      <div class="bg-green-400 h-2" style="width: 20%;"></div>
      <span class="absolute right-0 text-xs text-gray-400">${borrowLimit}</span>
    </div>
  
    <div class="grid grid-cols-2 gap-6 mt-10">
      <div class="bg-gray-800 p-6 rounded-lg">
        <h2 class="text-xl font-bold">Supply Markets</h2>
        <table class="w-full mt-4">
          <thead>
            <tr class="text-left">
              <th>Assets</th><th>APY</th><th>Wallet</th><th>Collateral</th>
            </tr>
          </thead>
          <tbody>
            {#each supplyMarkets as market}
              <tr>
                <td>{market.name}</td>
                <td>{market.apy}</td>
                <td>{market.wallet}</td>
                <td><input type="checkbox" checked={market.collateral} class="toggle"></td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
      <div class="bg-gray-800 p-6 rounded-lg">
        <h2 class="text-xl font-bold">Borrow Markets</h2>
        <table class="w-full mt-4">
          <thead>
            <tr class="text-left">
              <th>Assets</th><th>APY</th><th>Wallet</th><th>% of Limit</th>
            </tr>
          </thead>
          <tbody>
            {#each borrowMarkets as market}
              <tr>
                <td>{market.name}</td>
                <td>{market.apy}</td>
                <td>{market.wallet}</td>
                <td><div class="bg-red-400 h-2 w-{market.limit}"></div></td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
    </div>
  </div>
  