<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SPECIAL SUPERFAN</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f7f7f7;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 400px;
            text-align: center;
            transition: opacity 0.3s ease;
            position: relative;
        }
        .hidden {
            display: none;
        }
        input[type="text"], input[type="email"], input[type="password"], input[type="date"], input[type="tel"], input[type="file"], textarea, select {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            background-color: #007BFF;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .alert {
            color: red;
            margin-top: 10px;
        }
        .profile-info {
            text-align: left;
            margin-bottom: 20px;
        }
        .profile-info img {
            max-width: 100%;
            border-radius: 5px;
        }
        h2 {
            color: #333;
            margin-bottom: 20px;
        }
        p {
            color: #555;
        }
        .nav-button {
            background-color: #28a745;
        }
        .nav-button:hover {
            background-color: #218838;
        }
        .payment-button {
            background-color: #ffc107;
        }
        .payment-button:hover {
            background-color: #e0a800;
        }
        header {
            background-color: #343a40;
            color: white;
            padding: 10px 0;
            position: absolute;
            top: -40px;
            left: 0;
            width: 100%;
            border-top-left-radius: 10px;
            border-top-right-radius: 10px;
        }
    </style>
    <script>
        function showPage(pageId) {
            const pages = document.querySelectorAll('.container');
            pages.forEach(page => {
                page.classList.add('hidden');
            });
            document.getElementById(pageId).classList.remove('hidden');
        }

        function signup() {
            const name = document.getElementById('signup-name').value;
            const email = document.getElementById('signup-email').value;
            const password = document.getElementById('signup-password').value;

            if (name && email && password) {
                showPage('thank-you-page');
            } else {
                document.getElementById('signup-alert').textContent = 'Please fill in all fields.';
                document.getElementById('signup-alert').classList.remove('hidden');
            }
        }

        function login() {
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;

            if (email && password) {
                showPage('thank-you-page');
            } else {
                document.getElementById('login-alert').textContent = 'Please fill in all fields.';
                document.getElementById('login-alert').classList.remove('hidden');
            }
        }

        function submitInfo() {
            const fullName = document.getElementById('full-name').value;
            const dob = document.getElementById('dob').value;
            const gender = document.getElementById('gender').value;
            const contactNumber = document.getElementById('contact-number').value;
            const email = document.getElementById('info-email').value;
            const mailingAddress = document.getElementById('mailing-address').value;
            const profilePicture = document.getElementById('profile-picture').files[0];
            const membershipType = document.getElementById('membership-type').value;
            const communicationMethod = document.getElementById('communication-method').value;

            if (fullName && dob && gender && contactNumber && email && mailingAddress && profilePicture && membershipType && communicationMethod) {
                document.getElementById('profile-full-name').textContent = fullName;
                document.getElementById('profile-dob').textContent = dob;
                document.getElementById('profile-gender').textContent = gender;
                document.getElementById('profile-contact-number').textContent = contactNumber;
                document.getElementById('profile-email').textContent = email;
                document.getElementById('profile-mailing-address').textContent = mailingAddress;
                document.getElementById('profile-membership-type').textContent = membershipType;
                document.getElementById('profile-communication-method').textContent = communicationMethod;

                const reader = new FileReader();
                reader.onload = function(e) {
                    document.getElementById('profile-picture-img').src = e.target.result;
                }
                reader.readAsDataURL(profilePicture);

                showPage('fan-club-info-page');
            } else {
                document.getElementById('info-alert').textContent = 'Please fill in all fields.';
                document.getElementById('info-alert').classList.remove('hidden');
            }
        }

        function submitFanClubInfo() {
            const howHear = document.getElementById('how-hear').value;
            const hopes = document.getElementById('hopes').value;
            const suggestions = document.getElementById('suggestions').value;

            if (howHear && hopes && suggestions) {
                showPage('superfans-page');
            } else {
                document.getElementById('fan-club-info-alert').textContent = 'Please fill in all fields.';
                document.getElementById('fan-club-info-alert').classList.remove('hidden');
            }
        }

        function confirmSubscription() {
            const agreement = document.getElementById('subscription-agreement').checked;

            if (agreement) {
                showPage('payment-page');
            } else {
                document.getElementById('subscription-alert').textContent = 'Please agree to the subscription fee.';
                document.getElementById('subscription-alert').classList.remove('hidden');
            }
        }

        function showPaymentDetails(method) {
            document.getElementById('cashapp-info').classList.add('hidden');
            document.getElementById('paypal-info').classList.add('hidden');
            document.getElementById('crypto-info').classList.add('hidden');
            if (method === 'cashapp') {
                document.getElementById('cashapp-info').classList.remove('hidden');
            } else if (method === 'paypal') {
                document.getElementById('paypal-info').classList.remove('hidden');
            } else if (method === 'crypto') {
                document.getElementById('crypto-info').classList.remove('hidden');
            }
        }

        function showEmailInfo() {
            showPage('email-page');
        }

        function submitPaymentScreenshot() {
            const paymentScreenshot = document.getElementById('payment-screenshot').files[0];

            if (paymentScreenshot) {
                showPage('thank-you-subscription-page');
            } else {
                document.getElementById('payment-screenshot-alert').textContent = 'Please upload your payment screenshot.';
                document.getElementById('payment-screenshot-alert').classList.remove('hidden');
            }
        }
    </script>
</head>
<body>
    <div id="signup-page" class="container">
        <header>SPECIAL SUPERFAN</header>
        <h2>Sign up to support your favorite creators</h2>
        <input type="text" id="signup-name" placeholder="Name" required>
        <input type="email" id="signup-email" placeholder="Email" required>
        <input type="password" id="signup-password" placeholder="Password" required>
        <button class="nav-button" onclick="signup()">Sign Up</button>
        <p>Already have an account? <a href="#" onclick="showPage('login-page')">Log in</a></p>
        <p class="alert hidden" id="signup-alert"></p>
    </div>

    <div id="login-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Log in</h2>
        <input type="email" id="login-email" placeholder="Email" required>
        <input type="password" id="login-password" placeholder="Password" required>
        <button class="nav-button" onclick="login()">Log In</button>
        <p>Don't have an account? <a href="#" onclick="showPage('signup-page')">Sign up</a></p>
        <p class="alert hidden" id="login-alert"></p>
    </div>

    <div id="thank-you-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Thank You!</h2>
        <p>I just wanted to take a moment to say thank you to all my amazing fans! Your support means the world to me, and I couldn't do this without you. You all are the best, and I'm so grateful for each and every one of you.</p>
        <p>Lots of love, </p>
        <button class="nav-button" onclick="showPage('info-page')">Next</button>
    </div>

    <div id="info-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Fill in your information</h2>
        <input type="text" id="full-name" placeholder="Full Name" required>
        <input type="date" id="dob" placeholder="Date of Birth" required>
        <select id="gender">
            <option value="" disabled selected>Gender</option>
            <option value="Male">Male</option>
            <option value="Female">Female</option>
            <option value="Other">Other</option>
        </select>
        <input type="tel" id="contact-number" placeholder="Contact Number" required>
        <input type="email" id="info-email" placeholder="Email Address" required>
        <input type="text" id="mailing-address" placeholder="Mailing Address" required>
        <input type="file" id="profile-picture" accept="image/*" required>
        <h3>Membership Details</h3>
        <select id="membership-type">
            <option value="Regular">Regular</option>
            <option value="Premium">Premium</option>
        </select>
        <select id="communication-method">
            <option value="" disabled selected>Preferred Method of Communication</option>
            <option value="Email">Email</option>
            <option value="Phone">Phone</option>
            <option value="Mail">Mail</option>
        </select>
        <button class="nav-button" onclick="submitInfo()">Submit</button>
        <p class="alert hidden" id="info-alert"></p>
    </div>

    <div id="fan-club-info-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Fan Club-Specific Information</h2>
        <textarea id="how-hear" placeholder="How did you hear about the fan club?" rows="3" required></textarea>
        <textarea id="hopes" placeholder="What do you hope to gain from joining the fan club?" rows="3" required></textarea>
        <textarea id="suggestions" placeholder="Any suggestions for activities or events?" rows="3" required></textarea>
        <button class="nav-button" onclick="submitFanClubInfo()">Submit</button>
        <p class="alert hidden" id="fan-club-info-alert"></p>
    </div>

    <div id="superfans-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>❤️‍🔥What my superfans grant ⬇️</h2>
        <p>📍Daily New Content (over 500 sexy & nudes pics including vids you get immediate access to upon subscription)</p>
        <p>📍B/G and Solo content (PPV)</p>
        <p>📌I sell my panties</p>
        <p>📍Twerk videos</p>
        <p>❣️Video call</p>
        <p>❤️Hookup</p>
        <p>🥰 Unlimited talk</p>
        <p>❣️Masturbating video</p>
        <p>❣️Random meeting</p>
        <p>📌One on one messaging 24/7 with you</p>
        <button class="nav-button" onclick="showPage('subscription-page')">Next</button>
    </div>

    <div id="subscription-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Profile Information</h2>
        <div class="profile-info">
            <p><strong>Full Name:</strong> <span id="profile-full-name"></span></p>
            <p><strong>Date of Birth:</strong> <span id="profile-dob"></span></p>
            <p><strong>Gender:</strong> <span id="profile-gender"></span></p>
            <p><strong>Contact Number:</strong> <span id="profile-contact-number"></span></p>
            <p><strong>Email Address:</strong> <span id="profile-email"></span></p>
            <p><strong>Mailing Address:</strong> <span id="profile-mailing-address"></span></p>
            <p><strong>Membership Type:</strong> <span id="profile-membership-type"></span></p>
            <p><strong>Preferred Method of Communication:</strong> <span id="profile-communication-method"></span></p>
            <img id="profile-picture-img" src="#" alt="Profile Picture">
        </div>
        <p>To proceed with your subscription, please confirm your agreement to the subscription amount.</p>
        <p>
            <label>
                <input type="checkbox" id="subscription-agreement">
                By checking this box, you acknowledge and agree to the annual subscription fee of $30.
            </label>
        </p>
        <button class="nav-button" onclick="confirmSubscription()">Next</button>
        <p class="alert hidden" id="subscription-alert"></p>
    </div>

    <div id="payment-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Payment Mode</h2>
        <p>Please select your payment method:</p>
        <button class="payment-button" onclick="showPaymentDetails('cashapp')">Cash App</button>
        <button class="payment-button" onclick="showPaymentDetails('paypal')">PayPal</button>
        <button class="payment-button" onclick="showPaymentDetails('crypto')">Crypto</button>
        <div id="payment-details">
            <p id="cashapp-info" class="hidden">$SoutherFusion</p>
            <p id="paypal-info" class="hidden">M.howe30@yahoo.com</p>
            <p id="crypto-info" class="hidden">13CVQWXmyHA1YgcH9JDUq7BWkZGfcdKEoN</p>
        </div>
        <button class="nav-button" onclick="showPage('email-page')">Next</button>
    </div>

    <div id="email-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Payment Confirmation</h2>
        <p>Please forward all payment screenshots to the following email address:</p>
        <p><strong>mandymayfan@gmail.com</strong></p>
        <input type="file" id="payment-screenshot" accept="image/*" required>
        <button class="nav-button" onclick="submitPaymentScreenshot()">Submit</button>
        <p class="alert hidden" id="payment-screenshot-alert"></p>
    </div>

    <div id="thank-you-subscription-page" class="container hidden">
        <header>SPECIAL SUPERFAN</header>
        <h2>Thank You for Subscribing!</h2>
        <p>We have received your subscription request and payment screenshot. Thank you for subscribing to Super Fans! We will review your submission and provide you with exclusive access shortly.</p>
    </div>
</body>
</html>
