<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Landing Page with Countdown</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron&display=swap');
        
        body {
            font-family: 'Orbitron', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #000;
            color: #0f0;
        }

        .container {
            text-align: center;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #0f0;
        }

        .countdown {
            display: flex;
            justify-content: center;
            gap: 1rem;
            font-size: 2rem;
            font-weight: bold;
            color: #0f0;
        }

        .countdown div {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .countdown span {
            font-size: 1rem;
            color: #0f0;
        }

        footer {
            margin-top: 2rem;
            font-size: 0.9rem;
            color: #0f0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1></h1>
        <div class="countdown">
            <div>
                <div id="days">0</div>
                <span>Days</span>
            </div>
            <div>
                <div id="hours">0</div>
                <span>Hours</span>
            </div>
            <div>
                <div id="minutes">0</div>
                <span>Minutes</span>
            </div>
            <div>
                <div id="seconds">0</div>
                <span>Seconds</span>
            </div>
        </div>
    </div>

    <footer>
        &copy; FILTHY-WRLD.INC NO RIGHTS RESERVED.
    </footer>

    <script>
        // Set the countdown to start from 30 days from now
        const now = new Date();
        const launchDate = new Date(now.getTime() + 30 * 24 * 60 * 60 * 1000);

        // Update the countdown every second
        const countdownInterval = setInterval(() => {
            const currentTime = new Date().getTime();
            const timeLeft = launchDate - currentTime;

            if (timeLeft < 0) {
                clearInterval(countdownInterval);
                document.querySelector('.countdown').innerHTML = "<h2>We're Live!</h2>";
                return;
            }

            const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);

            document.getElementById('days').innerText = days;
            document.getElementById('hours').innerText = hours;
            document.getElementById('minutes').innerText = minutes;
            document.getElementById('seconds').innerText = seconds;
        }, 1000);
    </script>
</body>
</html>
