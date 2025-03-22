<script>
/*Credit Score part*/
    let score = 750; 
    let scoreRange = "Average";
    let showPopup = false; 

    $: {
        if (score >= 750) scoreRange = "Excellent";
        else if (score >= 600) scoreRange = "Good";
        else if (score >= 500) scoreRange = "Average";
        else scoreRange = "Poor";
    }

    function togglePopup() {
        showPopup = !showPopup;
    }

    /* Gauge Rotation Calculation */
    // Calculate rotation angle for pointer (mapping score 300-850 to -90 to 90 degrees)
    $: rotation = `rotate(${((score - 300) / 750) * 180 - 90}deg)`;
</script>

<style>
    .background-video {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -1;
    }

    .dark-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5); 
        z-index: 0;
    }

    .page-container {
        position: relative;
        color: white;
        text-align: center;
        overflow-y: auto;
        scroll-behavior: smooth;
    }

    nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 20px;
        background: rgba(0, 0, 0, 0.6);
        position: fixed;
        width: 100%;
        top: 0;
        left: 0;
        z-index: 100;
    }

    nav a {
        color: white;
        text-decoration: none;
        margin: 0 15px;
        font-size: 18px;
    }

    .sign-up-btn {
        background: gold;
        padding: 10px 20px;
        border-radius: 5px;
        color: black;
        font-weight: bold;
    }

    .hero {
        padding: 450px 20px 120px;
    }

    .hero h1 {
        font-size: 3rem;
        font-weight: bold;
    }

    .hero p {
        font-size: 1.2rem;
        opacity: 0.8;
    }

    .section {
        padding: 100px 20px;
        background: rgba(0, 0, 0, 0.35);
        margin: 20px 0;
        border-radius: 10px;
        max-width: 90%;
        margin-left: auto;
        margin-right: auto;
    }

/* Credit Score Widget */
    .credit-score-container {
        text-align: center;
        background: rgba(0, 0, 0, 0.8);
        padding: 20px;
        border-radius: 15px;
        max-width: 600px;
        width: 600px;
        margin: auto;
        color: white;
    }

    .gauge-container {
        position: relative;
        width: 250px;
        height: 150px;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 0px 173px;
    }

    .pointer {
        position: absolute;
        left: 50%;
        bottom: 0;
        width: 6px;
        height: 100px;
        background: rgb(255, 255, 255);
        border-radius: 3px;
        transform-origin: bottom;
        transition: transform 0.5s ease-in-out;
    }

    .labels {
        text-align: center;
        margin-top: 10px;
        font-weight: bold;
    }

    .ranges {
        display: flex;
        justify-content: space-between;
        margin-top: 5px;
        margin-bottom: 15px;
    }

    .range {
        font-size: 12px;
        padding: 3px 8px;
        border-radius: 5px;
    }

    .poor { background: #E74C3C; color: rgb(0, 0, 0); }
    .average { background: #ff7b00; color: black; }
    .good { background: #F1C40F; color: rgb(0, 0, 0); }
    .excellent { background: #2ECC71; color: rgb(0, 0, 0); }

    .popup {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background: white;
        padding: 20px;
        border-radius: 10px;
        width: 300px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
        z-index: 100;
        color: black;
    }

    .popup-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        z-index: 99;
    }

    .close-btn {
        padding: 8px 15px;
        background: red;
        color: white;
        border: none;
        cursor: pointer;
        border-radius: 5px;
    }

    .leaderboard {
        background: rgba(0, 0, 0, 0.6);
        padding: 20px;
        border-radius: 10px;
    }

    table {
        width: 100%;
        border-collapse: collapse;
    }

    th, td {
        padding: 10px;
        border-bottom: 1px solid white;
    }

    th {
        background: rgba(255, 255, 255, 0.2);
    }

    .highlight-gold {
        font-weight: bold;
        color: gold;
    }

    .highlight-silver {
        font-weight: bold;
        color: silver;
    }

    .highlight-bronze {
        font-weight: bold;
        color: brown;
    }
</style>

<video class="background-video" autoplay loop muted>
    <source src="/videos/background.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<div class="dark-overlay"></div>

<nav>
    <div>
        <a href="/">Home</a>
        <a href="/profile/update_profile">Profile</a>
        <a href="/missions">Missions</a>
        <a href="/borrow-lend">Borrowing & Lending</a>
    </div>
    <a href="/signup" class="sign-up-btn">Sign Up</a>
</nav>

<div class="page-container">
    
    <div class="hero">
        <h1>Gamified Blockchain System</h1>
        <p>Blockchain made simple: Learn! Build! Succeed!</p>
    </div>

<!-- Credit Score Section -->
    <div class="credit-score-container">
        <h2>Credit Score: {score}</h2>
        
        <div class="gauge-container">
            <!-- Gauge Background -->
            <svg viewBox="0 0 100 50" width="200" height="100">
                <!-- Define Gradient -->
                <defs>
                    <linearGradient id="gaugeGradient">
                        <stop offset="0%" stop-color="#E74C3C" />  <!-- Red (Poor) -->
                        <stop offset="25%" stop-color="#FF7B00" /> <!-- Orange -->
                        <stop offset="50%" stop-color="#F1C40F" /> <!-- Yellow (Average) -->
                        <stop offset="75%" stop-color="#2ECC71" /> <!-- Green (Good) -->
                    </linearGradient>
                </defs>
            
                <!-- Gauge Arc Path -->
                <path d="M10,50 A40,40 0 0,1 90,50" 
                    fill="none" 
                    stroke="url(#gaugeGradient)" 
                    stroke-width="10" />
            </svg>
        
            <!-- Pointer -->
            <div class="pointer" style="transform: translateX(-50%) {rotation};"></div>
        </div>
        
        <!-- Score Labels -->
        <div class="labels">
            <p>{scoreRange}</p>
        </div>
        
        <!-- Range Indicators -->
        <div class="ranges">
            <span class="range poor">Poor <br> (500-)</span>
            <span class="range average">Average <br> (500 - 600)</span>
            <span class="range good">Good <br> (600 - 750)</span>
            <span class="range excellent">Excellent <br> (750+)</span>
        </div>

        <button on:click={togglePopup}>View Credit Score Factors</button>
    </div>

    {#if showPopup}
        <div 
            class="popup-overlay" 
            on:click={togglePopup} 
            tabindex="0" 
            role="button" 
            on:keydown={(e) => e.key === 'Enter' || e.key === ' ' ? togglePopup() : null}
        ></div>

        <div class="popup">
            <h3>Credit Score Factors</h3>
            <ul>
                <li>📜 <strong>Payment History</strong> - 35%</li>
                <li>💰 <strong>Amounts Owed</strong> - 30%</li>
                <li>⏳ <strong>Length of Credit History</strong> - 15%</li>
                <li>🆕 <strong>New Credit</strong> - 10%</li>
                <li>📊 <strong>Credit Mix</strong> - 10%</li>
            </ul>
            <button class="close-btn" on:click={togglePopup}>Close</button>
        </div>
    {/if}

<!-- Leaderboard Section -->
    <div class="section leaderboard">
        <h2>Leaderboard</h2>
        <table>
            <thead>
                <tr>
                    <th>Ranking</th>
                    <th>Name</th>
                    <th>Score</th>
                    <th>Wallet Age</th>
                    <th>Region</th>
                </tr>
            </thead>
            <tbody>
                <tr class="highlight-gold">
                    <td>#1</td>
                    <td>David Stampson</td>
                    <td>5800</td>
                    <td>10Y 2M</td>
                    <td>USA</td>
                </tr>
                <tr class="highlight-silver">
                    <td>#2</td>
                    <td>Evan Stephen</td>
                    <td>4200</td>
                    <td>8Y 4M</td>
                    <td>UK</td>
                </tr>
                <tr class="highlight-bronze">
                    <td>#3</td>
                    <td>Peter Parker</td>
                    <td>3700</td>
                    <td>7Y 6M</td>
                    <td>CANADA</td>
                </tr>
                <tr>
                    <td>#4</td>
                    <td>Hiroshi Tanaka</td>
                    <td>3450</td>
                    <td>13Y 5M</td>
                    <td>JAPAN</td>
                </tr>
                <tr>
                    <td>#5</td>
                    <td>Oliver Thompson</td>
                    <td>3300</td>
                    <td>12Y 6M</td>
                    <td>UK</td>
                </tr>
                <tr>
                    <td>#6</td>
                    <td>Evan Stephen</td>
                    <td>4200</td>
                    <td>8Y 4M</td>
                    <td>UK</td>
                </tr>
                <tr>
                    <td>#7</td>
                    <td>Peter Parker</td>
                    <td>3700</td>
                    <td>7Y 6M</td>
                    <td>CANADA</td>
                </tr>
                <tr>
                    <td>#8</td>
                    <td>Hiroshi Tanaka</td>
                    <td>3450</td>
                    <td>13Y 5M</td>
                    <td>JAPAN</td>
                </tr>
                <tr>
                    <td>#9</td>
                    <td>Oliver Thompson</td>
                    <td>3300</td>
                    <td>12Y 6M</td>
                    <td>UK</td>
                </tr>
                <tr>
                    <td>#10</td>
                    <td>Oliver Thompson</td>
                    <td>3300</td>
                    <td>12Y 6M</td>
                    <td>UK</td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
