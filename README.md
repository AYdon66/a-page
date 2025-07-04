
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>AY Page</title>
    <style>
        :root {
            --bg-color: #f4f4f4;
            --text-color: #333;
            --card-bg: white;
            --accent-color: #0a3d62;
        }

        body.dark-mode {
            --bg-color: #1e1e1e;
            --text-color: #ddd;
            --card-bg: #2c2c2c;
        }

        body,
        html {
            margin: 0;
            font-family: Arial, sans-serif;
            background: var(--bg-color);
            color: var(--text-color);
            transition: background 0.3s, color 0.3s;
        }

        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: var(--accent-color);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2em;
            z-index: 9999;
        }

        .container {
            padding: 20px;
            max-width: 600px;
            margin: 0 auto;
            background: var(--card-bg);
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            margin-top: 40px;
            transition: background 0.3s;
        }

        h1,
        h2 {
            text-align: center;
            color: var(--accent-color);
        }

        p {
            text-align: center;
            line-height: 1.6;
        }

        .input-group {
            margin-bottom: 15px;
        }

        .input-group label {
            display: block;
            margin-bottom: 5px;
        }

        .input-group input,
        .input-group textarea {
            width: 100%;
            padding: 8px;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: var(--accent-color);
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 4px;
        }

        .toggle-dark {
            text-align: center;
            margin-top: 10px;
        }

        .result {
            text-align: center;
            margin-top: 10px;
            font-weight: bold;
        }

        .contact-info {
            text-align: center;
            margin-top: 20px;
        }

        .contact-info a {
            color: var(--accent-color);
            text-decoration: none;
        }

        .profile-img {
            display: block;
            margin: 0 auto 15px auto;
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--accent-color);
        }
    </style>
</head>

<body>

    <div id="splash" class="splash-screen">
        Redirecting.....
    </div>

    <div class="container">
        <h1>AY PAGE</h1>
        <p>This is my personal project containing a simple calculator, a BMI calculator, my contact info, and a splash
            message.</p>

        <div class="toggle-dark">
            <button onclick="toggleDarkMode()">Toggle Dark Mode</button>
        </div>

        <h2>About Me</h2>
        <img src="my image.jpg" alt="Profile Image" class="profile-img" />
        <p>
            Hi, welcome to my page! I’m a student at the Federal University of Technology, Akure,
            currently studying in the Department of Forestry and Wood Technology.
            I chose Web Development as my Entrepreneurship (ENT) trade because I believe in its potential to take me
            far.
            Through building websites, I aim to meet the needs and goals of both myself and future clients.
        </p>

        <h2>SIMPLE CALCULATOR</h2>
        <div class="input-group">
            <label>First number:</label>
            <input type="number" id="num1" />
        </div>
        <div class="input-group">
            <label>Second number:</label>
            <input type="number" id="num2" />
        </div>
        <div class="input-group">
            <button onclick="calculate('+')">ADD</button>
            <button onclick="calculate('-')">SUBTRACT</button>
            <button onclick="calculate('*')">MULTIPLY</button>
            <button onclick="calculate('/')">DIVIDE</button>
        </div>
        <div class="result" id="calcResult"></div>

        <h2>BMI Checker</h2>
        <div class="input-group">
            <label>Height (in meters):</label>
            <input type="number" step="0.01" id="height" />
        </div>
        <div class="input-group">
            <label>Weight (in kilograms):</label>
            <input type="number" id="weight" />
        </div>
        <button onclick="checkBMI()">Calculate BMI</button>
        <div class="result" id="bmiResult"></div>

        <h2>Contact Me</h2>
        <form id="contactForm" onsubmit="submitContact(event)">
            <div class="input-group">
                <label for="name">Name:</label>
                <input type="text" id="name" required />
            </div>
            <div class="input-group">
                <label for="email">Email:</label>
                <input type="email" id="email" required />
            </div>
            <div class="input-group">
                <label for="message">Message:</label>
                <textarea id="message" rows="5" required></textarea>
            </div>
            <button type="submit">Send Message</button>
            <div class="result" id="contactResult"></div>
        </form>

        <div class="contact-info">
            <p><strong>Phone:</strong> <a href="tel:08139733208">08139733208</a></p>
            <p><strong>WhatsApp:</strong> <a href="https://wa.me/2348139733208" target="_blank">Chat on WhatsApp</a></p>
        </div>
    </div>

    <script>
        // Splash screen
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('splash').style.display = 'none';
            }, 2000);
        });

        function toggleDarkMode() {
            document.body.classList.toggle('dark-mode');
        }

        function calculate(operator) {
            const num1 = parseFloat(document.getElementById("num1").value);
            const num2 = parseFloat(document.getElementById("num2").value);
            let result = '';

            if (isNaN(num1) || isNaN(num2)) {
                result = 'Please enter valid numbers';
            } else {
                switch (operator) {
                    case '+': result = num1 + num2; break;
                    case '-': result = num1 - num2; break;
                    case '*': result = num1 * num2; break;
                    case '/': result = num2 !== 0 ? num1 / num2 : 'Cannot divide by zero'; break;
                }
            }
            document.getElementById("calcResult").innerText = result;
        }

        function checkBMI() {
            const height = parseFloat(document.getElementById("height").value);
            const weight = parseFloat(document.getElementById("weight").value);
            let result = '';

            if (isNaN(height) || isNaN(weight) || height <= 0) {
                result = 'Please enter valid height and weight';
            } else {
                const bmi = weight / (height * height);
                result = `Your BMI is ${bmi.toFixed(2)} - `;
                if (bmi < 18.5) result += 'Underweight';
                else if (bmi < 24.9) result += 'Normal weight';
                else if (bmi < 29.9) result += 'Overweight';
                else result += 'Obese';
            }
            document.getElementById("bmiResult").innerText = result;
        }

        function submitContact(event) {
            event.preventDefault();

            const name = document.getElementById('name').value.trim();
            const email = document.getElementById('email').value.trim();
            const message = document.getElementById('message').value.trim();

            if (!name || !email || !message) {
                document.getElementById('contactResult').innerText = 'Please fill in all fields.';
                return;
            }

            const phoneNumber = "2348139733208";
            const text = `Hello AY GADGETS, my name is ${name}.\nEmail: ${email}\nMessage: ${message}`;
            const whatsappURL = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(text)}`;
            window.open(whatsappURL, '_blank');

            document.getElementById('contactResult').innerText = `Redirecting to WhatsApp...`;
            document.getElementById('contactForm').reset();
        }
    </script>

</body>

</html>
