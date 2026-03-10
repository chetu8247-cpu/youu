<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Surprise!</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Outfit:wght@300;400;600&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --primary: #ff758c;
            --secondary: #ff7eb3;
            --glass: rgba(255, 255, 255, 0.1);
        }

        * { box-sizing: border-box; transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); }

        body, html {
            margin: 0; padding: 0; min-height: 100vh;
            font-family: 'Outfit', sans-serif;
            background: #0f0c29;
            background: linear-gradient(to bottom, #24243e, #302b63, #0f0c29);
            color: white; overflow-x: hidden;
        }

        /* Hero Section */
        #hero-screen {
            height: 100vh; display: flex; justify-content: center; align-items: center;
            flex-direction: column; text-align: center;
        }

        .glass-card {
            background: var(--glass); backdrop-filter: blur(15px);
            padding: 50px; border-radius: 40px; border: 1px solid rgba(255,255,255,0.1);
            box-shadow: 0 25px 50px rgba(0,0,0,0.5); width: 90%; max-width: 500px;
        }

        .cake-icon { font-size: 80px; animation: float 3s infinite ease-in-out; display: inline-block; }
        @keyframes float { 0%, 100% { transform: translateY(0) rotate(0); } 50% { transform: translateY(-20px) rotate(5deg); } }

        h1 { font-family: 'Dancing Script', cursive; font-size: 3.5rem; margin: 10px 0; color: var(--secondary); }

        /* Buttons */
        .btn-container { margin-top: 30px; position: relative; height: 120px; }
        #yes-btn {
            background: linear-gradient(45deg, #ff758c, #ff7eb3);
            color: white; border: none; padding: 15px 50px;
            font-size: 1.5rem; border-radius: 50px; cursor: pointer; font-weight: 600;
            box-shadow: 0 10px 20px rgba(255, 117, 140, 0.4);
        }
        #no-btn {
            background: transparent; color: #aaa; border: 1px solid #444;
            padding: 8px 20px; border-radius: 50px; cursor: pointer; position: absolute;
        }

        /* Memory Section (Hidden until click) */
        #memory-vault {
            display: none; padding: 60px 20px; text-align: center;
            max-width: 1000px; margin: 0 auto; opacity: 0;
        }

        .personal-note {
            font-family: 'Dancing Script', cursive; font-size: 2rem;
            max-width: 600px; margin: 0 auto 50px; line-height: 1.4;
            color: #ffd1d1; text-shadow: 0 0 10px rgba(255,255,255,0.2);
        }

        /* Photo Gallery Grid */
        .gallery {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px; perspective: 1000px;
        }

        .photo-card {
            background: white; padding: 12px; border-radius: 10px;
            transform: rotate(calc(var(--r) * 1deg));
            transition: 0.3s; box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }
        .photo-card:hover { transform: scale(1.05) rotate(0deg) translateY(-10px); z-index: 10; }
        
        /* UPDATED: Custom sizing for your vertical photo */
        .photo-card img { 
            width: 100%; 
            height: auto; 
            max-height: 450px; /* Limits the height so it doesn't take over the screen */
            object-fit: contain; /* Shows the whole photo */
            background-color: #f9f9f9; /* Soft background color for any spacing */
            border-radius: 5px; 
        }
        
        .photo-caption { color: #333; margin-top: 10px; font-weight: 600; font-size: 0.9rem; }

        .reveal { animation: fadeIn 1.5s forwards; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body>

    <section id="hero-screen">
        <div class="glass-card">
            <div class="cake-icon">🎂</div>
            <h1 id="bday-title">Happy Birthday!</h1>
            <p>I put together something special just for you. Ready to see our favorite moments?</p>
            
            <div class="btn-container">
                <button id="yes-btn" onclick="revealMemories()">YES, SHOW ME! ✨</button>
                <button id="no-btn" onmouseover="dodge()">No thanks</button>
            </div>
        </div>
    </section>

    <section id="memory-vault">
        <h2 style="font-size: 3rem; margin-bottom: 10px;">🎉 Cheers to You!</h2>
        
        <p class="personal-note">
            "To my favorite human: Thank you for all the laughs, the late-night chats, and for being exactly who you are. 
            May this year be as bright and beautiful as your smile! ❤️"
        </p>

        <div class="gallery">
            <div class="photo-card" style="--r: -3">
                <img src="https://images.unsplash.com/photo-1513151233558-d860c5398176?w=500" alt="Special photo">
                <p class="photo-caption">Day 1 Vibes 📸</p>
            </div>
            
            </div>

        <button onclick="location.reload()" style="margin-top: 80px; background: none; border: 1px solid #fff; color: #fff; padding: 10px 20px; border-radius: 30px; cursor: pointer; opacity: 0.6;">Start Over</button>
    </section>

    <script>
        // Personalization
        const name = new URLSearchParams(window.location.search).get('name') || "Bestie";
        document.getElementById('bday-title').innerText = `Happy Birthday, ${name}!`;

        // Runaway Button logic
        function dodge() {
            const btn = document.getElementById('no-btn');
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 50);
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // Reveal Logic
        function revealMemories() {
            // Confetti Blast
            confetti({
                particleCount: 150,
                spread: 70,
                origin: { y: 0.6 },
                colors: ['#ff758c', '#ff7eb3', '#ffffff']
            });

            // Smooth Transition
            document.getElementById('hero-screen').style.display = 'none';
            const vault = document.getElementById('memory-vault');
            vault.style.display = 'block';
            setTimeout(() => {
                vault.classList.add('reveal');
                window.scrollTo({ top: 0, behavior: 'smooth' });
            }, 100);

            // Continuous background confetti
            setInterval(() => {
                confetti({
                    particleCount: 5,
                    angle: 60,
                    spread: 55,
                    origin: { x: 0 },
                    colors: ['#ff7eb3']
                });
                confetti({
                    particleCount: 5,
                    angle: 120,
                    spread: 55,
                    origin: { x: 1 },
                    colors: ['#ff758c']
                });
            }, 3000);
        }
    </script>
</body>
</html>
