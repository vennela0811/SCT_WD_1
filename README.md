# SCT_WD_1
"""
✨ Gen Z Navigation Menu ✨
no cap this is bussin fr fr 💅
"""

from flask import Flask, render_template_string

app = Flask(__name__)

# HTML template with Gen Z aesthetic vibes
TEMPLATE = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>vibes only 💅</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;600;700&family=Outfit:wght@300;500;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --neon-pink: #ff006e;
            --neon-blue: #3a86ff;
            --neon-yellow: #ffbe0b;
            --neon-purple: #8338ec;
            --neon-green: #06ffa5;
            --dark-bg: #0d0221;
            --card-bg: #1a0b2e;
        }

        body {
            font-family: 'Outfit', sans-serif;
            background: var(--dark-bg);
            background-image: 
                radial-gradient(circle at 20% 50%, rgba(255, 0, 110, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(58, 134, 255, 0.15) 0%, transparent 50%),
                radial-gradient(circle at 40% 20%, rgba(131, 56, 236, 0.15) 0%, transparent 50%);
            min-height: 300vh;
            color: #fff;
            overflow-x: hidden;
            padding-top: 100px;
        }

        /* Animated background blobs */
        .blob {
            position: fixed;
            border-radius: 50%;
            filter: blur(60px);
            opacity: 0.3;
            animation: float 20s infinite ease-in-out;
            pointer-events: none;
            z-index: 0;
        }

        .blob1 {
            width: 300px;
            height: 300px;
            background: var(--neon-pink);
            top: 10%;
            left: 10%;
            animation-delay: 0s;
        }

        .blob2 {
            width: 250px;
            height: 250px;
            background: var(--neon-blue);
            top: 60%;
            right: 10%;
            animation-delay: 5s;
        }

        .blob3 {
            width: 200px;
            height: 200px;
            background: var(--neon-purple);
            bottom: 20%;
            left: 50%;
            animation-delay: 10s;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            25% { transform: translate(30px, -30px) scale(1.1); }
            50% { transform: translate(-20px, 20px) scale(0.9); }
            75% { transform: translate(40px, 10px) scale(1.05); }
        }

        /* Navigation Menu - FIXED */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(13, 2, 33, 0.8);
            backdrop-filter: blur(20px) saturate(180%);
            border-bottom: 3px solid var(--neon-pink);
            z-index: 1000;
            box-shadow: 0 8px 32px rgba(255, 0, 110, 0.3);
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Fredoka', sans-serif;
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--neon-pink), var(--neon-purple), var(--neon-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: -1px;
            cursor: pointer;
            animation: rainbow 3s linear infinite;
            background-size: 200% 200%;
        }

        @keyframes rainbow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .nav-menu {
            display: flex;
            gap: 0.5rem;
            list-style: none;
        }

        .nav-link {
            position: relative;
            padding: 0.8rem 1.5rem;
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            font-size: 1rem;
            border-radius: 50px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid transparent;
            transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            display: flex;
            align-items: center;
            gap: 0.5rem;
            overflow: hidden;
        }

        /* Emoji icons */
        .nav-link::before {
            font-size: 1.2rem;
            transition: transform 0.3s ease;
        }

        .nav-link[data-emoji="home"]::before { content: "🏠"; }
        .nav-link[data-emoji="about"]::before { content: "👀"; }
        .nav-link[data-emoji="vibes"]::before { content: "✨"; }
        .nav-link[data-emoji="chat"]::before { content: "💬"; }
        .nav-link[data-emoji="slay"]::before { content: "💅"; }

        /* Hover effects with different colors for each link */
        .nav-link:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
        }

        .nav-link:hover::before {
            transform: rotate(15deg) scale(1.2);
        }

        .nav-link:nth-child(1):hover {
            border-color: var(--neon-pink);
            background: linear-gradient(135deg, var(--neon-pink), transparent);
            box-shadow: 0 10px 30px rgba(255, 0, 110, 0.5);
        }

        .nav-link:nth-child(2):hover {
            border-color: var(--neon-blue);
            background: linear-gradient(135deg, var(--neon-blue), transparent);
            box-shadow: 0 10px 30px rgba(58, 134, 255, 0.5);
        }

        .nav-link:nth-child(3):hover {
            border-color: var(--neon-yellow);
            background: linear-gradient(135deg, var(--neon-yellow), transparent);
            box-shadow: 0 10px 30px rgba(255, 190, 11, 0.5);
        }

        .nav-link:nth-child(4):hover {
            border-color: var(--neon-purple);
            background: linear-gradient(135deg, var(--neon-purple), transparent);
            box-shadow: 0 10px 30px rgba(131, 56, 236, 0.5);
        }

        .nav-link:nth-child(5):hover {
            border-color: var(--neon-green);
            background: linear-gradient(135deg, var(--neon-green), transparent);
            box-shadow: 0 10px 30px rgba(6, 255, 165, 0.5);
        }

        /* Active state */
        .nav-link.active {
            background: linear-gradient(135deg, var(--neon-pink), var(--neon-purple));
            border-color: var(--neon-pink);
            box-shadow: 0 5px 20px rgba(255, 0, 110, 0.4);
            transform: translateY(-3px);
        }

        /* Glowing cursor trail effect */
        .nav-link::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            border-radius: 50px;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.8), transparent);
            opacity: 0;
            transform: scale(0);
            transition: all 0.5s ease;
            pointer-events: none;
        }

        .nav-link:active::after {
            opacity: 1;
            transform: scale(1.5);
            transition: all 0s;
        }

        /* Content sections */
        .section {
            position: relative;
            max-width: 1200px;
            margin: 3rem auto;
            padding: 3rem;
            background: rgba(26, 11, 46, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 30px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            z-index: 1;
        }

        .section h1 {
            font-family: 'Fredoka', sans-serif;
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--neon-pink), var(--neon-yellow), var(--neon-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
        }

        .section p {
            font-size: 1.2rem;
            line-height: 1.8;
            color: rgba(255, 255, 255, 0.9);
            font-weight: 300;
        }

        .badge {
            display: inline-block;
            padding: 0.5rem 1rem;
            background: linear-gradient(135deg, var(--neon-purple), var(--neon-pink));
            border-radius: 50px;
            font-weight: 600;
            margin: 1rem 0.5rem 0 0;
            font-size: 0.9rem;
            box-shadow: 0 5px 15px rgba(255, 0, 110, 0.3);
        }

        /* Mobile hamburger */
        .hamburger {
            display: none;
            flex-direction: column;
            gap: 6px;
            cursor: pointer;
            padding: 0.5rem;
        }

        .hamburger span {
            width: 30px;
            height: 3px;
            background: linear-gradient(90deg, var(--neon-pink), var(--neon-blue));
            border-radius: 3px;
            transition: all 0.3s ease;
        }

        .hamburger:hover span {
            background: linear-gradient(90deg, var(--neon-yellow), var(--neon-green));
        }

        /* Scroll indicator */
        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--neon-pink), var(--neon-yellow), var(--neon-blue), var(--neon-purple), var(--neon-green));
            background-size: 200% 100%;
            animation: gradient-shift 3s linear infinite;
            z-index: 1001;
            transform-origin: left;
        }

        @keyframes gradient-shift {
            0% { background-position: 0% 0%; }
            100% { background-position: 200% 0%; }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-menu {
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                flex-direction: column;
                background: rgba(13, 2, 33, 0.95);
                backdrop-filter: blur(20px);
                padding: 1rem;
                gap: 0.8rem;
                max-height: 0;
                overflow: hidden;
                transition: max-height 0.4s ease;
            }

            .nav-menu.active {
                max-height: 500px;
            }

            .section h1 {
                font-size: 2.5rem;
            }
        }

        /* Sparkle effect on scroll */
        @keyframes sparkle {
            0%, 100% { opacity: 0; transform: scale(0) rotate(0deg); }
            50% { opacity: 1; transform: scale(1) rotate(180deg); }
        }
    </style>
</head>
<body>
    <!-- Background blobs -->
    <div class="blob blob1"></div>
    <div class="blob blob2"></div>
    <div class="blob blob3"></div>

    <!-- Scroll progress bar -->
    <div class="scroll-progress" id="scrollProgress"></div>

    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <div class="logo">vibes™</div>
            
            <div class="hamburger" id="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </div>

            <ul class="nav-menu" id="navMenu">
                <li><a href="#home" class="nav-link active" data-emoji="home">home</a></li>
                <li><a href="#about" class="nav-link" data-emoji="about">about</a></li>
                <li><a href="#vibes" class="nav-link" data-emoji="vibes">vibes</a></li>
                <li><a href="#chat" class="nav-link" data-emoji="chat">chat</a></li>
                <li><a href="#slay" class="nav-link" data-emoji="slay">slay</a></li>
            </ul>
        </div>
    </nav>

    <!-- Content -->
    <section id="home" class="section">
        <h1>no cap this is bussin 🔥</h1>
        <p>periodt. this navigation menu stays glued to the top while u scroll - it's giving main character energy fr fr. watch how the menu items absolutely slay with those neon vibes when you hover over them 💅</p>
        <span class="badge">✨ aesthetic ✨</span>
        <span class="badge">💯 vibes only</span>
        <span class="badge">🚫🧢 no cap</span>
    </section>

    <section id="about" class="section">
        <h1>the tea sis ☕</h1>
        <p>okay so basically this whole vibe is chef's kiss. we got neon colors that hit different, smooth animations that are lowkey fire, and each menu item has its own personality. the whole aesthetic is very "that girl" meets cyberpunk meets my spotify wrapped 🎨</p>
        <p style="margin-top: 1rem;">the nav stays fixed at the top - it's literally rent free in your browser window bestie. scroll down and peep how it never leaves. that's commitment 💍</p>
        <span class="badge">😤 understood the assignment</span>
        <span class="badge">👁️👄👁️ immaculate</span>
    </section>

    <section id="vibes" class="section">
        <h1>it's giving ✨main character✨</h1>
        <p>the color palette? absolutely unhinged in the best way. pink, blue, yellow, purple, green - we said yes to everything and it WORKS. those floating blobs in the background? *chef's kiss* they're literally just vibing and i respect that energy 🌈</p>
        <p style="margin-top: 1rem;">hover over the menu items and watch them do a lil bounce - it's the attention to detail for me 💫 each one lights up with its own neon glow like they're the main character (because they are)</p>
        <span class="badge">🎨 art™</span>
        <span class="badge">🌟 built different</span>
    </section>

    <section id="chat" class="section">
        <h1>the deets 📱</h1>
        <p>real talk: this whole thing is coded in Python with Flask serving the vibes. it's responsive too so it looks fire on your phone AND your laptop. the hamburger menu on mobile? clean. the gradient progress bar at the top? elite behavior 📊</p>
        <p style="margin-top: 1rem;">we're using Fredoka and Outfit fonts because they're quirky and fun - none of that boring corporate font nonsense. life's too short for times new roman bestie 💅</p>
        <span class="badge">💻 tech savvy</span>
        <span class="badge">📱 mobile friendly</span>
        <span class="badge">🎯 on point</span>
    </section>

    <section id="slay" class="section">
        <h1>period. 💅</h1>
        <p>if you made it this far, congrats you're living your best life. this nav menu isn't just functional, it's a whole MOOD. it's colorful, it's playful, it's unapologetically extra and we're here for it 🎉</p>
        <p style="margin-top: 1rem;">the glassmorphism? the neon borders? the emoji icons? the chaos? yes. to. all. of. it. this is what peak performance looks like and i will not be taking questions at this time 😌✨</p>
        <span class="badge">👑 royalty behavior</span>
        <span class="badge">💎 luxury vibes</span>
        <span class="badge">🔥 absolutely slaying</span>
    </section>

    <script>
        // Scroll progress bar
        const scrollProgress = document.getElementById('scrollProgress');
        window.addEventListener('scroll', () => {
            const windowHeight = document.documentElement.scrollHeight - window.innerHeight;
            const scrolled = (window.scrollY / windowHeight) * 100;
            scrollProgress.style.transform = `scaleX(${scrolled / 100})`;
        });

        // Active nav link on scroll
        const sections = document.querySelectorAll('.section');
        const navLinks = document.querySelectorAll('.nav-link');

        window.addEventListener('scroll', () => {
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                if (window.scrollY >= sectionTop - 150) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === `#${current}`) {
                    link.classList.add('active');
                }
            });
        });

        // Smooth scroll
        navLinks.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const target = document.querySelector(link.getAttribute('href'));
                window.scrollTo({
                    top: target.offsetTop - 100,
                    behavior: 'smooth'
                });

                // Close mobile menu
                if (window.innerWidth <= 768) {
                    document.getElementById('navMenu').classList.remove('active');
                }
            });
        });

        // Mobile menu toggle
        const hamburger = document.getElementById('hamburger');
        const navMenu = document.getElementById('navMenu');
        
        hamburger.addEventListener('click', () => {
            navMenu.classList.toggle('active');
        });

        // Close menu when clicking outside
        document.addEventListener('click', (e) => {
            if (!e.target.closest('nav')) {
                navMenu.classList.remove('active');
            }
        });

        // Sparkle effect on scroll (optional easter egg)
        let scrollTimeout;
        window.addEventListener('scroll', () => {
            document.body.style.cursor = 'progress';
            clearTimeout(scrollTimeout);
            scrollTimeout = setTimeout(() => {
                document.body.style.cursor = 'default';
            }, 100);
        });
    </script>
</body>
</html>
"""

@app.route('/')
def home():
    """serve the vibes 💅"""
    return render_template_string(TEMPLATE)


if __name__ == '__main__':
    print("🔥 starting the vibes server... no cap this bout to be bussin 🔥")
    print("📱 navigate to http://127.0.0.1:5000 for the full experience ✨")
    print("💅 ctrl+c to stop slaying\n")
    
    app.run(debug=True, host='0.0.0.0', port=5000)
