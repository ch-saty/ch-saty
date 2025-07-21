<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Android Developer Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            min-height: 100vh;
            color: #ffffff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Glassmorphism Card */
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 30px;
            margin: 20px 0;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            position: relative;
            overflow: hidden;
        }

        .glass-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.05), transparent);
            transform: rotate(45deg);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) rotate(45deg); }
            50% { transform: translateX(100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }

        /* Header Section */
        .header {
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 3px solid rgba(0, 255, 255, 0.5);
            margin-bottom: 20px;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.3);
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { box-shadow: 0 0 20px rgba(0, 255, 255, 0.3); }
            to { box-shadow: 0 0 40px rgba(0, 255, 255, 0.6); }
        }

        .name-title {
            font-size: 3rem;
            font-weight: bold;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #00ffff, #ff00ff, #ffff00);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: textShimmer 3s ease-in-out infinite;
        }

        @keyframes textShimmer {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .subtitle {
            font-size: 1.5rem;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 20px;
        }

        .typing-text {
            font-size: 1.2rem;
            color: #00ff88;
            border-right: 2px solid #00ff88;
            animation: typing 4s steps(40) infinite, blink 1s infinite;
            white-space: nowrap;
            overflow: hidden;
            display: inline-block;
            max-width: 100%;
        }

        @keyframes typing {
            0%, 10% { width: 0; }
            50%, 60% { width: 100%; }
            90%, 100% { width: 0; }
        }

        @keyframes blink {
            0%, 50% { border-color: #00ff88; }
            51%, 100% { border-color: transparent; }
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .stat-card {
            background: rgba(0, 255, 255, 0.05);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(0, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 255, 255, 0.3);
        }

        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #00ffff;
            margin-bottom: 5px;
        }

        .stat-label {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.7);
        }

        /* Tech Stack */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .tech-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .tech-item:hover {
            transform: scale(1.05);
            background: rgba(0, 255, 255, 0.1);
            border-color: rgba(0, 255, 255, 0.3);
        }

        .tech-icon {
            width: 50px;
            height: 50px;
            margin-bottom: 10px;
            filter: drop-shadow(0 0 10px rgba(0, 255, 255, 0.5));
        }

        .tech-name {
            font-size: 0.9rem;
            color: rgba(255, 255, 255, 0.8);
            text-align: center;
        }

        /* Connect Section */
        .connect-grid {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            margin: 30px 0;
        }

        .connect-item {
            display: flex;
            align-items: center;
            padding: 15px 25px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 25px;
            text-decoration: none;
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .connect-item:hover {
            transform: translateY(-3px);
            background: rgba(0, 255, 255, 0.1);
            box-shadow: 0 5px 20px rgba(0, 255, 255, 0.3);
        }

        .connect-icon {
            width: 25px;
            height: 25px;
            margin-right: 10px;
        }

        /* Section Headers */
        .section-header {
            font-size: 2rem;
            font-weight: bold;
            margin: 40px 0 20px 0;
            text-align: center;
            position: relative;
            color: #ffffff;
        }

        .section-header::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, #00ffff, #ff00ff);
            border-radius: 2px;
        }

        /* Android Robot Animation */
        .android-robot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background: #3DDC84;
            border-radius: 50%;
            animation: float 3s ease-in-out infinite;
            z-index: 1000;
            cursor: pointer;
        }

        .android-robot::before {
            content: '🤖';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 30px;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .name-title {
                font-size: 2rem;
            }
            
            .subtitle {
                font-size: 1.2rem;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .connect-grid {
                flex-direction: column;
                align-items: center;
            }
        }

        .quote {
            font-style: italic;
            font-size: 1.2rem;
            text-align: center;
            color: rgba(255, 255, 255, 0.8);
            margin: 20px 0;
            position: relative;
        }

        .quote::before {
            content: '"';
            font-size: 3rem;
            color: #00ffff;
            position: absolute;
            left: -20px;
            top: -10px;
        }

        .quote::after {
            content: '"';
            font-size: 3rem;
            color: #00ffff;
            position: absolute;
            right: -20px;
            bottom: -20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <div class="glass-card">
            <div class="header">
                <img src="https://github.com/ch-saty.png" alt="Profile" class="profile-img" onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUwIiBoZWlnaHQ9IjE1MCIgdmlld0JveD0iMCAwIDE1MCAxNTAiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxyZWN0IHdpZHRoPSIxNTAiIGhlaWdodD0iMTUwIiBmaWxsPSIjMzMzIiByeD0iNzUiLz4KPHN2ZyB4PSI0NSIgeT0iNDAiIHdpZHRoPSI2MCIgaGVpZ2h0PSI2MCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSIjNjY2Ij4KPHBhdGggZD0iTTEyIDEyYzIuMjEgMCA0LTEuNzkgNC00cy0xLjc5LTQtNC00LTQgMS43OS00IDQgMS43OSA0IDQgNHptMCAyYy0yLjY3IDAtOCAxLjM0LTggNHYyaDE2di0yYzAtMi42Ni01LjMzLTQtOC00eiIvPgo8L3N2Zz4KPC9zdmc+'">
                <h1 class="name-title">Satyam Choudhary</h1>
                <p class="subtitle">🚀 Android Developer & Competitive Coder</p>
                <div class="typing-text">Building the future, one app at a time...</div>
                <div class="quote">Code is poetry written in logic</div>
            </div>
        </div>

        <!-- Stats Section -->
        <div class="glass-card">
            <h2 class="section-header">📊 Developer Stats</h2>
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number" id="profile-views">999+</div>
                    <div class="stat-label">Profile Views</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">5+</div>
                    <div class="stat-label">Years Experience</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">50+</div>
                    <div class="stat-label">Projects Built</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">∞</div>
                    <div class="stat-label">Coffee Consumed</div>
                </div>
            </div>
        </div>

        <!-- About Section -->
        <div class="glass-card">
            <h2 class="section-header">🎯 About Me</h2>
            <div style="text-align: center; line-height: 1.8; font-size: 1.1rem; position: relative; z-index: 2;">
                <p>🔥 Passionate Android Developer crafting exceptional mobile experiences</p>
                <p>💡 Competitive Programmer with a love for algorithmic challenges</p>
                <p>🌟 Always exploring cutting-edge technologies and best practices</p>
                <p>📱 Specialized in Flutter, Kotlin, and modern Android development</p>
                <p>🎨 Believer in clean code, elegant architecture, and pixel-perfect UI</p>
            </div>
        </div>

        <!-- Tech Stack -->
        <div class="glass-card">
            <h2 class="section-header">🛠️ Tech Arsenal</h2>
            <div class="tech-grid">
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/android/android-original.svg" alt="Android">
                    <div class="tech-name">Android</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="Flutter">
                    <div class="tech-name">Flutter</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/kotlin/kotlin-original.svg" alt="Kotlin" onerror="this.src='data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNTAiIGhlaWdodD0iNTAiIHZpZXdCb3g9IjAgMCA1MCA1MCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHJlY3Qgd2lkdGg9IjUwIiBoZWlnaHQ9IjUwIiBmaWxsPSIjNzM3N0FEIi8+Cjx0ZXh0IHg9IjUwJSIgeT0iNTAlIiBkb21pbmFudC1iYXNlbGluZT0ibWlkZGxlIiB0ZXh0LWFuY2hvcj0ibWlkZGxlIiBmaWxsPSJ3aGl0ZSIgZm9udC1zaXplPSIxMiI+S1Q8L3RleHQ+Cjwvc3ZnPg=='">
                    <div class="tech-name">Kotlin</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java">
                    <div class="tech-name">Java</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" alt="Firebase">
                    <div class="tech-name">Firebase</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="JavaScript">
                    <div class="tech-name">JavaScript</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="Python">
                    <div class="tech-name">Python</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg" alt="React">
                    <div class="tech-name">React</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original.svg" alt="Node.js">
                    <div class="tech-name">Node.js</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" alt="MongoDB">
                    <div class="tech-name">MongoDB</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="Git">
                    <div class="tech-name">Git</div>
                </div>
                <div class="tech-item">
                    <img class="tech-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="C++">
                    <div class="tech-name">C++</div>
                </div>
            </div>
        </div>

        <!-- GitHub Stats -->
        <div class="glass-card">
            <h2 class="section-header">📈 GitHub Analytics</h2>
            <div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; align-items: center;">
                <img src="https://github-readme-stats.vercel.app/api?username=ch-saty&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117" alt="GitHub Stats" style="border-radius: 10px;">
                <img src="https://github-readme-streak-stats.herokuapp.com/?user=ch-saty&theme=tokyonight&hide_border=true&background=0d1117" alt="GitHub Streak" style="border-radius: 10px;">
                <img src="https://github-readme-stats.vercel.app/api/top-langs?username=ch-saty&show_icons=true&theme=tokyonight&layout=compact&hide_border=true&bg_color=0d1117" alt="Top Languages" style="border-radius: 10px;">
            </div>
        </div>

        <!-- Connect Section -->
        <div class="glass-card">
            <h2 class="section-header">🌐 Let's Connect</h2>
            <div class="connect-grid">
                <a href="mailto:satyamchoudhary8183@gmail.com" class="connect-item">
                    <svg class="connect-icon" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
                    </svg>
                    Email
                </a>
                <a href="https://linkedin.com/in/satyam-choudary" class="connect-item" target="_blank">
                    <svg class="connect-icon" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                    </svg>
                    LinkedIn
                </a>
                <a href="https://instagram.com/_choudharysatyam" class="connect-item" target="_blank">
                    <svg class="connect-icon" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                    </svg>
                    Instagram
                </a>
                <a href="https://leetcode.com/_satyamchoudhary" class="connect-item" target="_blank">
                    <svg class="connect-icon" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.817 2.133 8.046-.069l2.582-2.556a1.374 1.374 0 0 0-.904-2.314c-.398.012-.797-.027-1.174-.115a3.27 3.27 0 0 1-.769-.3 4.264 4.264 0 0 1-1.019-.725l-2.477-2.42a1.374 1.374 0 0 0-1.943.001l-.556.545a1.374 1.374 0 0 0 .001 1.943l1.043 1.021a1.374 1.374 0 0 0 1.943-.001c.484-.472.395-1.338-.228-1.76a.613.613 0 0 0-.593.021c-.027.016-.055.024-.082.045l-.963.945a.274.274 0 0 1-.387 0l-.532-.52a.274.274 0 0 1 0-.388l.963-.944c.349-.341.92-.364 1.292-.047.433.369.467 1.02.052 1.437l-1.043 1.02a.548.548 0 0 1-.775.001l-1.556-1.522a.548.548 0 0 1-.001-.776l.556-.545a.548.548 0 0 1 .775-.001l2.477 2.42c.2.196.434.357.69.473.313.142.65.231.997.257.399.03.8-.018 1.174-.115l-2.582 2.556c-1.774 1.749-4.582 1.774-6.374.069l-4.277-4.193a4.195 4.195 0 0 1-.897-1.285 4.12 4.12 0 0 1-.247-.717 3.896 3.896 0 0 1-.044-1.323 3.736 3.736 0 0 1 .858-1.488l3.854-4.126a1.374 1.374 0 0 0 .904-2.314z"/>
                    </svg>
                    LeetCode
                </a>
            </div>
        </div>
    </div>

    <!-- Floating Android Robot -->
    <div class="android-robot" onclick="this.style.animation='none'; setTimeout(()=>this.style.animation='float 3s ease-in-out infinite', 100);"></div>

    <script>
        // Profile views counter animation
        function animateCounter() {
            const counter = document.getElementById('profile-views');
            let count = 0;
            const target = 999;
            const increment = target / 100;
            
            const timer = setInterval(() => {
                count += increment;
                if (count >= target) {
                    count = target;
                    clearInterval(timer);
                    counter.textContent = target + '+';
                } else {
                    counter.textContent = Math.floor(count);
                }
            }, 20);
        }

        // Start counter animation on load
        window.addEventListener('load', animateCounter);

        // Add click effects to tech items
        document.querySelectorAll('.tech-item').forEach(item => {
            item.addEventListener('click', function() {
                this.style.transform = 'scale(1.1)';
                this.style.transition = 'transform 0.2s ease';
                setTimeout(() => {
                    this.style.transform = 'scale(1.05)';
                }, 200);
            });
        });

        // Add floating particles effect
        function createParticle() {
            const particle = document.createElement('div');
            particle.style.cssText = `
                position: fixed;
                width: 4px;
                height: 4px;
                background: linear-gradient(45deg, #00ffff, #ff00ff);
                border-radius: 50%;
                pointer-events: none;
                z-index: 1;
                opacity: 0.7;
                animation: floatUp 4s linear forwards;
                left: ${Math.random() * 100}vw;
                top: 100vh;
            `;
            
            document.body.appendChild(particle);
            
            setTimeout(() => {
                particle.remove();
            }, 4000);
        }

        // Add CSS for particle animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes floatUp {
                0% {
                    transform: translateY(0) rotate(0deg);
                    opacity: 0.7;
                }
                100% {
                    transform: translateY(-100vh) rotate(360deg);
                    opacity: 0;
                }
            }
        `;
        document.head.appendChild(style);

        // Create particles periodically
        setInterval(createParticle, 800);

        // Add smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add typing effect restart on scroll
        const typingElement = document.querySelector('.typing-text');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'none';
                    setTimeout(() => {
                        entry.target.style.animation = 'typing 4s steps(40) infinite, blink 1s infinite';
                    }, 100);
                }
            });
        });

        observer.observe(typingElement);

        // Add mouse trail effect
        let mouseTrail = [];
        document.addEventListener('mousemove', (e) => {
            mouseTrail.push({x: e.clientX, y: e.clientY, time: Date.now()});
            
            // Limit trail length
            if (mouseTrail.length > 20) {
                mouseTrail.shift();
            }
            
            // Create trail element
            const trail = document.createElement('div');
            trail.style.cssText = `
                position: fixed;
                width: 6px;
                height: 6px;
                background: radial-gradient(circle, rgba(0,255,255,0.8) 0%, transparent 70%);
                border-radius: 50%;
                pointer-events: none;
                z-index: 9999;
                left: ${e.clientX - 3}px;
                top: ${e.clientY - 3}px;
                animation: trailFade 0.8s ease-out forwards;
            `;
            
            document.body.appendChild(trail);
            setTimeout(() => trail.remove(), 800);
        });

        // Add trail fade animation
        const trailStyle = document.createElement('style');
        trailStyle.textContent = `
            @keyframes trailFade {
                0% { 
                    opacity: 1; 
                    transform: scale(1);
                }
                100% { 
                    opacity: 0; 
                    transform: scale(0.3);
                }
            }
        `;
        document.head.appendChild(trailStyle);
    </script>
</body>
</html>
