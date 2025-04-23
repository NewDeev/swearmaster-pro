<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SwearMaster Pro 🤬</title>
    <style>
        :root {
            --primary-color: #FF4136;
            --secondary-color: #FF851B;
            --accent-color: #FFDC00;
            --dark-color: #111111;
            --light-color: #f8f8f8;
        }

        body {
            font-family: 'Comic Sans MS', cursive, sans-serif;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
            margin: 0;
            background-color: var(--dark-color);
            background-image:
                radial-gradient(circle at 10% 20%, rgba(255, 65, 54, 0.2) 0%, transparent 20%),
                radial-gradient(circle at 90% 30%, rgba(255, 133, 27, 0.2) 0%, transparent 20%),
                radial-gradient(circle at 50% 80%, rgba(255, 220, 0, 0.2) 0%, transparent 20%);
            color: var(--light-color);
        }

        header {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 1rem;
            text-align: center;
            border-bottom: 3px solid var(--primary-color);
            position: relative;
        }

        .logo {
            font-size: 2.5rem;
            font-weight: bold;
            color: var(--accent-color);
            text-shadow: 2px 2px 0 var(--primary-color);
            margin: 0;
        }

        .logo span {
            color: var(--primary-color);
        }

        nav {
            display: flex;
            justify-content: center;
            gap: 1rem;
            padding: 1rem;
            background-color: rgba(0, 0, 0, 0.6);
            flex-wrap: wrap;
        }

        nav a {
            color: var(--light-color);
            text-decoration: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            transition: all 0.3s;
        }

        nav a:hover {
            background-color: var(--primary-color);
            transform: translateY(-2px);
        }

        .user-auth {
            position: absolute;
            right: 1rem;
            top: 1rem;
            display: flex;
            gap: 0.5rem;
        }

        .user-auth button {
            background-color: transparent;
            color: var(--light-color);
            border: 1px solid var(--light-color);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 0.8rem;
        }

        .user-auth button:hover {
            background-color: var(--primary-color);
            border-color: var(--primary-color);
        }

        .main-wrapper {
            display: flex;
            flex: 1;
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem;
            gap: 1rem;
        }

        .ad-column {
            width: 200px;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .page-content {
            flex: 1;
            min-width: 0;
        }

        .main-content {
            text-align: center;
            background-color: rgba(0, 0, 0, 0.7);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
            position: relative;
            border: 2px solid var(--primary-color);
            margin-bottom: 2rem;
        }

        h1 {
            color: var(--accent-color);
            margin-bottom: 1.5rem;
            font-size: 2rem;
            text-shadow: 2px 2px 0 var(--primary-color);
        }

        #name-input {
            width: 100%;
            padding: 0.8rem;
            margin-bottom: 1rem;
            border-radius: 5px;
            border: none;
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }

        #display {
            font-size: 1.8rem;
            margin: 1rem 0;
            min-height: 80px;
            padding: 1.5rem;
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            border: 1px dashed var(--secondary-color);
            color: var(--light-color);
        }

        .button-group {
            display: flex;
            gap: 1rem;
            justify-content: center;
            margin-top: 1rem;
        }

        button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 1rem 2rem;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 1px;
            box-shadow: 0 4px 0 darkred;
        }

        #resetBtn {
            background-color: #333;
            box-shadow: 0 4px 0 #111;
        }

        #resetBtn:hover {
            background-color: #444;
            box-shadow: 0 6px 0 #111;
        }

        button:hover {
            background-color: #ff2a1c;
            transform: translateY(-2px);
            box-shadow: 0 6px 0 darkred;
        }

        button:active {
            transform: translateY(2px);
            box-shadow: 0 2px 0 darkred;
        }

        button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        .loading-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            border-radius: 13px;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s;
        }

        .loading-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        .loader {
            border: 5px solid rgba(255, 255, 255, 0.1);
            border-top: 5px solid var(--accent-color);
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin-bottom: 1rem;
        }

        .loading-text {
            color: var(--accent-color);
            font-size: 1.2rem;
            text-align: center;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        .ad-space {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 1rem;
            border-radius: 10px;
            text-align: center;
            border: 1px dashed var(--secondary-color);
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .ad-space h3 {
            color: var(--accent-color);
            margin-top: 0;
            font-size: 1.2rem;
        }

        .ad-space p {
            margin: 0.5rem 0;
            font-size: 0.9rem;
        }

        .ad-space .ad-label {
            font-size: 0.7rem;
            color: rgba(255, 255, 255, 0.5);
            margin-top: auto;
        }

        .subscription {
            background-color: rgba(255, 65, 54, 0.2);
            padding: 1.5rem;
            border-radius: 10px;
            margin-top: 2rem;
            border: 1px solid var(--primary-color);
        }

        .subscription h2 {
            color: var(--accent-color);
            margin-top: 0;
        }

        .price {
            font-size: 2rem;
            color: var(--primary-color);
            font-weight: bold;
            margin: 1rem 0;
        }

        .subscribe-btn {
            background-color: var(--accent-color);
            color: var(--dark-color);
            padding: 0.8rem 1.5rem;
            font-size: 1rem;
            box-shadow: 0 4px 0 #ccb000;
        }

        .subscribe-btn:hover {
            background-color: #ffea00;
            box-shadow: 0 6px 0 #ccb000;
        }

        footer {
            background-color: rgba(0, 0, 0, 0.8);
            padding: 1.5rem;
            text-align: center;
            border-top: 3px solid var(--primary-color);
            margin-top: auto;
        }

        footer p {
            margin: 0;
            font-size: 1.2rem;
            color: var(--light-color);
        }

        .hidden {
            display: none;
        }

        .auth-form {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 2rem;
            border-radius: 10px;
            max-width: 400px;
            margin: 0 auto;
            border: 1px solid var(--primary-color);
        }

        .auth-form h2 {
            color: var(--accent-color);
            margin-top: 0;
            text-align: center;
        }

        .auth-form label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--accent-color);
        }

        .auth-form input {
            width: 100%;
            padding: 0.8rem;
            margin-bottom: 1rem;
            border-radius: 5px;
            border: none;
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
        }

        .auth-form button {
            width: 100%;
            margin-top: 1rem;
        }

        .account-info {
            background-color: rgba(0, 0, 0, 0.7);
            padding: 2rem;
            border-radius: 10px;
            max-width: 600px;
            margin: 0 auto;
            border: 1px solid var(--primary-color);
        }

        .account-info h2 {
            color: var(--accent-color);
            margin-top: 0;
        }

        .account-details {
            margin-top: 1rem;
        }

        .account-details p {
            margin: 0.5rem 0;
        }

        .account-details strong {
            color: var(--accent-color);
        }

        @media (max-width: 900px) {
            .main-wrapper {
                flex-direction: column;
            }

            .ad-column {
                width: 100%;
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: center;
            }

            .ad-space {
                width: calc(50% - 0.5rem);
                min-height: 150px;
            }

            .user-auth {
                position: static;
                justify-content: center;
                margin-top: 0.5rem;
            }
        }

        @media (max-width: 500px) {
            .ad-space {
                width: 100%;
            }

            .button-group {
                flex-direction: column;
            }

            button {
                width: 100%;
            }
        }
    </style>
</head>

<body>
    <header>
        <h1 class="logo">Swear<span>Master</span> Pro</h1>
        <div class="user-auth">
            <button id="loginBtn">Login</button>
            <button id="signupBtn">Sign Up</button>
            <button id="accountBtn" class="hidden">My Account</button>
            <button id="logoutBtn" class="hidden">Logout</button>
        </div>
    </header>

    <nav>
        <a href="#" class="nav-link" data-page="home">Home</a>
        <a href="#" class="nav-link" data-page="join">Join Us</a>
        <a href="#" class="nav-link" data-page="subscribe">Subscribe</a>
        <a href="#" class="nav-link" data-page="account" id="accountNav" class="hidden">My Account</a>
    </nav>

    <div class="main-wrapper">
        <!-- Left Ad Column -->
        <div class="ad-column">
            <div class="ad-space">
                <h3>Advertisement Space</h3>
                <p>Your ad could be here!</p>
                <p>Contact us for rates</p>
                <div class="ad-label">ADVERTISMENT</div>
            </div>
            <div class="ad-space">
                <h3>Premium Swear Package</h3>
                <p>Get the most offensive words!</p>
                <p>Only ₹99/month</p>
                <div class="ad-label">SPONSORED</div>
            </div>
        </div>

        <!-- Main Content Area -->
        <div class="page-content">
            <!-- Home Page -->
            <div class="page" id="home-page">
                <div class="main-content">
                    <h1>Swear Generator 🤬</h1>

                    <input type="text" id="name-input" placeholder="Enter name of the person..." required>

                    <div id="display">Enter a name and click Generate</div>

                    <div class="button-group">
                        <button id="generateBtn">Generate Swear</button>
                        <button id="resetBtn">Reset</button>
                    </div>

                    <div class="loading-overlay" id="loadingOverlay">
                        <div class="loader"></div>
                        <div class="loading-text">Generating the perfect insult...</div>
                    </div>
                </div>
            </div>

            <!-- Join Us Page -->
            <div id="join-page" class="page hidden">
                <div class="main-content">
                    <h1>Join Our Community</h1>
                    <p>Become part of the most offensive community on the internet!</p>

                    <div class="subscription">
                        <h2>Why Join?</h2>
                        <ul style="text-align: left; padding-left: 1.5rem;">
                            <li>Access to exclusive swear words</li>
                            <li>Custom insult generator</li>
                            <li>Anger management resources (just kidding)</li>
                            <li>Community forums</li>
                            <li>Monthly swear challenges</li>
                        </ul>
                    </div>
                </div>
            </div>

            <!-- Subscribe Page -->
            <div id="subscribe-page" class="page hidden">
                <div class="main-content">
                    <h1>Premium Subscription</h1>
                    <p>Upgrade your swearing game with our premium plans!</p>

                    <div class="subscription">
                        <h2>Basic Plan</h2>
                        <p>Perfect for casual swearers</p>
                        <div class="price">₹99/month</div>
                        <ul style="text-align: left; padding-left: 1.5rem;">
                            <li>100 premium swears per month</li>
                            <li>5 custom swear creations</li>
                            <li>Basic insult generator</li>
                            <li>Ad-supported</li>
                        </ul>
                        <button class="subscribe-btn">Subscribe Now</button>
                    </div>

                    <div class="subscription" style="background-color: rgba(255, 133, 27, 0.2); border-color: var(--secondary-color); margin-top: 2rem;">
                        <h2>Pro Plan</h2>
                        <p>For serious insult artists</p>
                        <div class="price" style="color: var(--secondary-color);">₹199/month</div>
                        <ul style="text-align: left; padding-left: 1.5rem;">
                            <li>Unlimited premium swears</li>
                            <li>20 custom swear creations</li>
                            <li>Advanced insult generator</li>
                            <li>Ad-free experience</li>
                            <li>Priority support</li>
                        </ul>
                        <button class="subscribe-btn">Subscribe Now</button>
                    </div>
                </div>
            </div>

            <!-- Account Page -->
            <div id="account-page" class="page hidden">
                <div class="main-content">
                    <div class="account-info">
                        <h2>My Account</h2>
                        <div class="account-details" id="accountDetails">
                            <p><strong>Username:</strong> <span id="account-username"></span></p>
                            <p><strong>Email:</strong> <span id="account-email"></span></p>
                            <p><strong>Membership:</strong> <span id="account-membership">Free</span></p>
                            <p><strong>Swears Generated:</strong> <span id="account-swears">0</span></p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Login Form -->
            <div id="login-page" class="page hidden">
                <div class="main-content">
                    <div class="auth-form">
                        <h2>Login</h2>
                        <form id="loginForm">
                            <label for="login-email">Email:</label>
                            <input type="email" id="login-email" required>

                            <label for="login-password">Password:</label>
                            <input type="password" id="login-password" required>

                            <button type="submit">Login</button>
                        </form>
                    </div>
                </div>
            </div>

            <!-- Signup Form -->
            <div id="signup-page" class="page hidden">
                <div class="main-content">
                    <div class="auth-form">
                        <h2>Sign Up</h2>
                        <form id="signupForm">
                            <label for="signup-username">Username:</label>
                            <input type="text" id="signup-username" required>

                            <label for="signup-email">Email:</label>
                            <input type="email" id="signup-email" required>

                            <label for="signup-password">Password:</label>
                            <input type="password" id="signup-password" required>

                            <button type="submit">Create Account</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>

        <!-- Right Ad Column -->
        <div class="ad-column">
            <div class="ad-space">
                <h3>Anger Management</h3>
                <p>Need help after using our generator?</p>
                <p>Call 1-800-CHILLOUT</p>
                <div class="ad-label">PUBLIC SERVICE</div>
            </div>
            <div class="ad-space">
                <h3>Custom Insults</h3>
                <p>Get personalized swears!</p>
                <p>Premium members only</p>
                <div class="ad-label">ADVERTISMENT</div>
            </div>
        </div>
    </div>

    <footer>
        <p>We help you swear better since 2023</p>
    </footer>

    <script>
        // Array of entries from your Excel file
        const entries = [
            "Bhosdike",
            "Maderchod",
            "Bhen ke lode",
            "Macchar ki jhant",
            "Gandu maa ki choot teri",
            "Randi ke tail",
            "Ghode ke lode",
            "Bhosad ke jhantoore",
            "Tatti ke tiile",
            "Kale lund ka muth",
            "Hulk se chude teri maa",
            "Bhusandi saand",
            "Sade hue chutad wale",
            "Baglundi randi",
            "Hazar lund ka chuda suar",
            "Bhosadpati ke chode",
            "Suar ki jhant",
            "Randi baaj",
            "Chutad dana",
            "Gand mein zanjeerein",
            "Lode mein chopstick",
            "Tatton ka paseena",
            "Jhant mein phassa muth",
            "Harri tatti ka keeda",
            "Kamzor lund ka muth",
            "Kutiya ka bhosda",
            "Pital ki gand",
            "Muth ka juice",
            "Gobar ka lund",
            "Kali choot ki jhant",
            "Katte tatton ka kofta",
            "Lund biryani",
            "Tatti ka halwa",
            "Tendue ke tatte",
            "Khargosh ka lund",
            "Betichod",
            "Chakke ke gand ka baal",
            "Randue ke lund ka condom",
            "Kutiya ke kale bobe",
            "Bhand randi ka choda",
            "Dariyai ghode ki gandi gand",
            "Bhosadike",
            "Bhen chod",
            "Bhadhava",
            "Chodu",
            "Chutiya",
            "Gaand",
            "Gaandu",
            "Gadha",
            "Bakland",
            "Lauda",
            "Lund",
            "Hijra",
            "Kuttiya",
            "Paad",
            "Randi",
            "Saala kutta",
            "Saali kutti",
            "Tatti",
            "Kamina",
            "Chut ke pasine mein talay huye bhajiye",
            "Chut ke dhakkan",
            "Chut ke gulam",
            "Chutiya ka bheja ghas khane gaya hai",
            "Choot marani ka",
            "Choot ka baal",
            "Chipkali ke jhaat ke baal",
            "Chipkali ke jhaat ke paseene",
            "Chipkali ke gaand ke pasine",
            "Chipkali ke chut ke pasine",
            "Chipkali ki bhigi chut",
            "Chinaal ke gadde ke nipple ke baal ke joon",
            "Chullu bhar muth mein doob mar",
            "Cuntmama",
            "Chhed",
            "Apni gaand mein muthi daal",
            "Apni lund choos",
            "Apni ma ko ja choos",
            "Bhen ke laude",
            "Bhen ke takke: Go and suck your sister’s balls",
            "Abla naari tera buble bhaari",
            "Bhonsri",
            "Bhadwe ka awlat",
            "Bhains ki aulad",
            "Buddha Khoosat",
            "Bol teri gand kaise maru",
            "Bur ki chatani",
            "Chunni",
            "Chinaal",
            "Chudai khana",
            "Chudan chuda",
            "Chut ka pujari",
            "Chut ka bhoot",
            "Gaand ka makhan",
            "Gaand main lassan",
            "Gaand main danda",
            "Gaand main keera",
            "Gaand mein bambu",
            "Gaandfat",
            "Pote kitne bhi bade ho, lund ke niche hi rehte hai",
            "Hazaar lund teri gaand main",
            "Jhat ke baal",
            "Jhaant ke pissu",
            "Kadak Mall",
            "Kali Choot Ke Safaid Jhaat",
            "Khotey ki aulda",
            "Kutte ka awlat",
            "Kutte ki jat",
            "Kutte ke tatte",
            "Kutte ke poot, teri maa ki choot",
            "Lavde ke bal",
            "Lund Chus: Suck dick",
            "Lund Ke Pasine",
            "Meri Gand Ka Khatmal: Bug of my Ass",
            "Moot, Mootna",
            "Najayaz paidaish",
            "Rundi khana",
            "Sadi hui gaand",
            "Teri gaand main kute ka lund",
            "Teri maa ka bhosda",
            "Teri maa ki chut",
            "Tere gaand mein keede paday",
            "Ullu ke pathe",
            "Muth laga kapda"

        ];

        // DOM elements
        const displayElement = document.getElementById('display');
        const generateBtn = document.getElementById('generateBtn');
        const resetBtn = document.getElementById('resetBtn');
        const nameInput = document.getElementById('name-input');
        const loadingOverlay = document.getElementById('loadingOverlay');
        const pages = document.querySelectorAll('.page');
        const navLinks = document.querySelectorAll('.nav-link');
        const loginBtn = document.getElementById('loginBtn');
        const signupBtn = document.getElementById('signupBtn');
        const accountBtn = document.getElementById('accountBtn');
        const logoutBtn = document.getElementById('logoutBtn');
        const accountNav = document.getElementById('accountNav');
        const loginForm = document.getElementById('loginForm');
        const signupForm = document.getElementById('signupForm');

        // User state
        let currentUser = null;

        // Check if user is logged in from localStorage
        function checkAuth() {
            const user = localStorage.getItem('swearUser');
            if (user) {
                currentUser = JSON.parse(user);
                updateAuthUI();
            }
        }

        // Update UI based on auth state
        function updateAuthUI() {
            if (currentUser) {
                loginBtn.classList.add('hidden');
                signupBtn.classList.add('hidden');
                accountBtn.classList.remove('hidden');
                logoutBtn.classList.remove('hidden');
                accountNav.classList.remove('hidden');

                // Update account info
                document.getElementById('account-username').textContent = currentUser.username;
                document.getElementById('account-email').textContent = currentUser.email;
                document.getElementById('account-swears').textContent = currentUser.swearsGenerated || 0;
            } else {
                loginBtn.classList.remove('hidden');
                signupBtn.classList.remove('hidden');
                accountBtn.classList.add('hidden');
                logoutBtn.classList.add('hidden');
                accountNav.classList.add('hidden');
            }
        }

        // Navigation functionality
        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const page = link.getAttribute('data-page');
                showPage(page);
            });
        });

        // Auth buttons
        loginBtn.addEventListener('click', () => showPage('login'));
        signupBtn.addEventListener('click', () => showPage('signup'));
        accountBtn.addEventListener('click', () => showPage('account'));
        logoutBtn.addEventListener('click', logout);

        function showPage(page) {
            pages.forEach(p => p.classList.add('hidden'));
            document.getElementById(`${page}-page`).classList.remove('hidden');
        }

        // Show home page by default
        showPage('home');

        // Generate swear functionality
        generateBtn.addEventListener('click', () => {
            const name = nameInput.value.trim();

            if (!name) {
                alert('Please enter a name first!');
                return;
            }

            // Disable button during loading
            generateBtn.disabled = true;
            resetBtn.disabled = true;

            // Show loading animation
            loadingOverlay.classList.add('active');
            displayElement.style.opacity = '0.5';

            // Show loading for 3 seconds
            setTimeout(() => {
                // Generate a random index
                const randomIndex = Math.floor(Math.random() * entries.length);

                // Display the random entry with the name
                displayElement.textContent = `${name} ${entries[randomIndex]}`;
                displayElement.style.opacity = '1';

                // Update swear count if logged in
                if (currentUser) {
                    currentUser.swearsGenerated = (currentUser.swearsGenerated || 0) + 1;
                    localStorage.setItem('swearUser', JSON.stringify(currentUser));
                    document.getElementById('account-swears').textContent = currentUser.swearsGenerated;
                }

                // Hide loading animation
                loadingOverlay.classList.remove('active');

                // Re-enable buttons
                generateBtn.disabled = false;
                resetBtn.disabled = false;
            }, 3000);
        });

        // Reset functionality
        resetBtn.addEventListener('click', () => {
            nameInput.value = '';
            displayElement.textContent = 'Enter a name and click Generate';
            displayElement.style.opacity = '1';
        });

        // Login form
        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;

            // Simple validation
            if (!email || !password) {
                alert('Please fill in all fields');
                return;
            }

            // Check if user exists
            const users = JSON.parse(localStorage.getItem('swearUsers') || []);
            const user = users.find(u => u.email === email && u.password === password);

            if (user) {
                currentUser = user;
                localStorage.setItem('swearUser', JSON.stringify(currentUser));
                updateAuthUI();
                showPage('home');
                alert('Login successful!');
            } else {
                alert('Invalid email or password');
            }
        });

        // Signup form
        signupForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const username = document.getElementById('signup-username').value;
            const email = document.getElementById('signup-email').value;
            const password = document.getElementById('signup-password').value;

            if (!username || !email || !password) {
                alert('Please fill in all fields');
                return;
            }

            // Check if user already exists
            const users = JSON.parse(localStorage.getItem('swearUsers') || []);
            if (users.some(u => u.email === email)) {
                alert('Email already registered');
                return;
            }

            // Create new user
            const newUser = {
                username,
                email,
                password,
                swearsGenerated: 0
            };

            users.push(newUser);
            localStorage.setItem('swearUsers', JSON.stringify(users));

            currentUser = newUser;
            localStorage.setItem('swearUser', JSON.stringify(currentUser));
            updateAuthUI();
            showPage('home');
            alert('Account created successfully!');
        });

        // Logout function
        function logout() {
            currentUser = null;
            localStorage.removeItem('swearUser');
            updateAuthUI();
            showPage('home');
        }

        // Subscription buttons
        document.querySelectorAll('.subscribe-btn').forEach(btn => {
            btn.addEventListener('click', () => {
                if (!currentUser) {
                    alert('Please login or sign up first');
                    showPage('login');
                    return;
                }
                alert('Redirecting to payment gateway... (This is a demo)');
            });
        });

        // Initialize
        checkAuth();
    </script>
</body>

</html>
