<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Developer Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
            color: #fff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        /* Animated Header */
        .header {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .title {
            font-size: 3em;
            font-weight: 900;
            background: linear-gradient(45deg, #00d4ff, #7c3aed, #ff006e);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 6s ease infinite;
            margin-bottom: 10px;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .subtitle {
            font-size: 1.3em;
            color: #a8dadc;
            animation: fadeInUp 1s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Glowing Line */
        .glow-line {
            height: 3px;
            background: linear-gradient(90deg, transparent, #00d4ff, #7c3aed, #ff006e, transparent);
            margin: 30px 0;
            animation: glow 2s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { opacity: 0.5; }
            50% { opacity: 1; }
        }

        /* Section */
        .section {
            margin: 50px 0;
            animation: slideIn 0.8s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-30px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .section-title {
            font-size: 1.8em;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 0;
            height: 3px;
            background: linear-gradient(90deg, #00d4ff, #7c3aed);
            animation: expandWidth 0.8s ease-out forwards;
        }

        @keyframes expandWidth {
            to { width: 100%; }
        }

        /* Tech Stack */
        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 25px;
        }

        .tech-item {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 212, 255, 0.3);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-weight: 600;
            transition: all 0.3s ease;
            cursor: pointer;
            animation: popIn 0.5s cubic-bezier(0.34, 1.56, 0.64, 1) backwards;
        }

        .tech-item:nth-child(1) { animation-delay: 0.1s; }
        .tech-item:nth-child(2) { animation-delay: 0.2s; }
        .tech-item:nth-child(3) { animation-delay: 0.3s; }
        .tech-item:nth-child(4) { animation-delay: 0.4s; }
        .tech-item:nth-child(5) { animation-delay: 0.5s; }
        .tech-item:nth-child(6) { animation-delay: 0.6s; }

        @keyframes popIn {
            from {
                opacity: 0;
                transform: scale(0.3) rotateZ(-10deg);
            }
            to {
                opacity: 1;
                transform: scale(1) rotateZ(0deg);
            }
        }

        .tech-item:hover {
            background: rgba(0, 212, 255, 0.15);
            border-color: #00d4ff;
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
        }

        /* Projects */
        .projects {
            display: grid;
            gap: 20px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(124, 58, 237, 0.4);
            padding: 25px;
            border-radius: 15px;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            animation: slideUp 0.6s ease-out backwards;
        }

        .project-card:nth-child(1) { animation-delay: 0.1s; }
        .project-card:nth-child(2) { animation-delay: 0.2s; }
        .project-card:nth-child(3) { animation-delay: 0.3s; }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transition: left 0.5s ease;
        }

        .project-card:hover::before {
            left: 100%;
        }

        .project-card:hover {
            background: rgba(255, 255, 255, 0.12);
            border-color: #00d4ff;
            transform: translateY(-8px);
            box-shadow: 0 20px 50px rgba(0, 212, 255, 0.25);
        }

        .project-title {
            font-size: 1.4em;
            margin-bottom: 8px;
            color: #00d4ff;
        }

        .project-desc {
            color: #ccc;
            margin-bottom: 12px;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tech-tag {
            background: rgba(0, 212, 255, 0.2);
            color: #00d4ff;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.85em;
            border: 1px solid rgba(0, 212, 255, 0.5);
        }

        /* Connect Section */
        .connect {
            text-align: center;
            margin-top: 60px;
        }

        .connect-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .connect-btn {
            background: linear-gradient(135deg, #00d4ff, #7c3aed);
            color: #000;
            padding: 12px 25px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 700;
            transition: all 0.3s ease;
            display: inline-block;
            border: 2px solid transparent;
            cursor: pointer;
        }

        .connect-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.4);
        }

        /* Floating Animation */
        .floating {
            animation: floating 3s ease-in-out infinite;
        }

        @keyframes floating {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        .emoji {
            font-size: 2em;
            display: inline-block;
            margin-right: 10px;
        }

        .footer {
            text-align: center;
            margin-top: 80px;
            padding-top: 20px;
            border-top: 1px solid rgba(0, 212, 255, 0.2);
            color: #888;
            animation: fadeInUp 1.5s ease-out;
        }

        .star {
            color: #ffd700;
            animation: twinkle 1.5s ease-in-out infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1 class="title floating">👨‍💻 Full-Stack Developer</h1>
            <p class="subtitle">Odoo × React Specialist</p>
            <div class="glow-line"></div>
            <p style="color: #a8dadc; margin-top: 20px; font-size: 1.05em;">Building powerful enterprise solutions with cutting-edge technology</p>
        </div>

        <!-- Tech Stack -->
        <div class="section">
            <h2 class="section-title">🛠️ Tech Stack</h2>
            <div class="tech-grid">
                <div class="tech-item">Python</div>
                <div class="tech-item">Odoo</div>
                <div class="tech-item">React</div>
                <div class="tech-item">JavaScript</div>
                <div class="tech-item">TypeScript</div>
                <div class="tech-item">PostgreSQL</div>
                <div class="tech-item">Tailwind CSS</div>
                <div class="tech-item">REST APIs</div>
                <div class="tech-item">Docker</div>
            </div>
        </div>

        <!-- What I Build -->
        <div class="section">
            <h2 class="section-title">⚡ What I Build</h2>
            <div class="tech-grid" style="grid-template-columns: 1fr;">
                <div class="tech-item" style="text-align: left;">⚙️ Custom Odoo modules & workflow automation</div>
                <div class="tech-item" style="text-align: left;">🎨 Modern React applications with stunning UIs</div>
                <div class="tech-item" style="text-align: left;">🔗 Seamless Odoo ↔ React integrations</div>
                <div class="tech-item" style="text-align: left;">📊 Enterprise solutions at scale</div>
            </div>
        </div>

        <!-- Featured Projects -->
        <div class="section">
            <h2 class="section-title">🚀 Featured Projects</h2>
            <div class="projects">
                <div class="project-card">
                    <div class="project-title">Project Name 1</div>
                    <div class="project-desc">React + Odoo Integration - Building seamless connections between frontend and ERP</div>
                    <div class="project-tech">
                        <span class="tech-tag">React</span>
                        <span class="tech-tag">Odoo API</span>
                        <span class="tech-tag">JavaScript</span>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-title">Project Name 2</div>
                    <div class="project-desc">Custom Odoo Module - Inventory management system with advanced automation</div>
                    <div class="project-tech">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Odoo</span>
                        <span class="tech-tag">PostgreSQL</span>
                    </div>
                </div>
                <div class="project-card">
                    <div class="project-title">Project Name 3</div>
                    <div class="project-desc">React Dashboard - Real-time analytics and monitoring platform</div>
                    <div class="project-tech">
                        <span class="tech-tag">React</span>
                        <span class="tech-tag">TypeScript</span>
                        <span class="tech-tag">Tailwind CSS</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Connect -->
        <div class="connect section">
            <h2 class="section-title">🤝 Let's Connect</h2>
            <div class="connect-links">
                <a href="#" class="connect-btn">LinkedIn</a>
                <a href="#" class="connect-btn">GitHub</a>
                <a href="#" class="connect-btn">Email</a>
                <a href="#" class="connect-btn">Portfolio</a>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p><span class="star">⭐</span> If you like my work, consider giving it a star! <span class="star">⭐</span></p>
        </div>
    </div>
</body>
</html>
