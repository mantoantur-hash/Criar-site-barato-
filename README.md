<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Criar Site por 15 Reais</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0e27 0%, #1a0b2e 50%, #16213e 100%);
            color: #fff;
            overflow-x: hidden;
            position: relative;
        }

        .rocket {
            position: fixed;
            width: 40px;
            height: 40px;
            opacity: 0.15;
            pointer-events: none;
            z-index: 1;
        }

        .rocket::before {
            content: '🚀';
            font-size: 30px;
            position: absolute;
        }

        @keyframes flyUp1 {
            0% { transform: translateY(100vh) rotate(45deg); }
            100% { transform: translateY(-100px) rotate(45deg); }
        }

        @keyframes flyUp2 {
            0% { transform: translateY(100vh) rotate(35deg); }
            100% { transform: translateY(-100px) rotate(35deg); }
        }

        @keyframes flyDiagonal {
            0% { transform: translate(-100px, 100vh) rotate(60deg); }
            100% { transform: translate(100vw, -100px) rotate(60deg); }
        }

        .rocket:nth-child(1) { left: 10%; animation: flyUp1 15s linear infinite; animation-delay: 0s; }
        .rocket:nth-child(2) { left: 30%; animation: flyUp2 20s linear infinite; animation-delay: 3s; }
        .rocket:nth-child(3) { left: 50%; animation: flyUp1 18s linear infinite; animation-delay: 6s; }
        .rocket:nth-child(4) { left: 70%; animation: flyUp2 22s linear infinite; animation-delay: 9s; }
        .rocket:nth-child(5) { left: 85%; animation: flyUp1 17s linear infinite; animation-delay: 12s; }
        .rocket:nth-child(6) { left: 20%; animation: flyDiagonal 25s linear infinite; animation-delay: 2s; }
        .rocket:nth-child(7) { left: 60%; animation: flyDiagonal 30s linear infinite; animation-delay: 8s; }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative;
            z-index: 10;
        }

        header {
            padding: 20px 0;
            text-align: center;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            background: linear-gradient(45deg, #00f5ff, #ff00ff, #00ff88);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero {
            text-align: center;
            padding: 80px 20px;
            min-height: 90vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 4.5rem);
            font-weight: 900;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #00f5ff, #ff00ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 10px rgba(0, 245, 255, 0.5)); }
            to { filter: drop-shadow(0 0 20px rgba(255, 0, 255, 0.8)); }
        }

        .hero h2 {
            font-size: clamp(1.2rem, 3vw, 2rem);
            font-weight: 300;
            margin-bottom: 15px;
            color: #a0a0ff;
        }

        .hero p {
            font-size: clamp(1rem, 2vw, 1.2rem);
            color: #ccc;
            margin-bottom: 40px;
            max-width: 600px;
        }

        .btn {
            display: inline-block;
            padding: 18px 50px;
            background: linear-gradient(45deg, #00f5ff, #ff00ff);
            color: #fff;
            text-decoration: none;
            border-radius: 50px;
            font-size: 1.2rem;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 0 30px rgba(0, 245, 255, 0.5);
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 0 50px rgba(255, 0, 255, 0.8);
        }

        .section {
            padding: 80px 20px;
        }

        .section-title {
            text-align: center;
            font-size: clamp(2rem, 4vw, 3rem);
            margin-bottom: 50px;
            background: linear-gradient(45deg, #00ff88, #00f5ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 40px;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, rgba(0, 245, 255, 0.1), rgba(255, 0, 255, 0.1));
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .card:hover::before {
            opacity: 1;
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: rgba(0, 245, 255, 0.5);
            box-shadow: 0 10px 40px rgba(0, 245, 255, 0.3);
        }

        .card-icon {
            font-size: 3rem;
            margin-bottom: 20px;
        }

        .card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: #00f5ff;
        }

        .card p {
            color: #ccc;
            line-height: 1.6;
        }

        .process {
            display: flex;
            flex-direction: column;
            gap: 30px;
            margin-top: 40px;
        }

        .process-step {
            display: flex;
            align-items: center;
            gap: 30px;
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            border-left: 5px solid #00f5ff;
            transition: all 0.3s ease;
        }

        .process-step:hover {
            background: rgba(255, 255, 255, 0.08);
            transform: translateX(10px);
        }

        .process-number {
            font-size: 3rem;
            font-weight: bold;
            color: #00f5ff;
            min-width: 80px;
        }

        .process-content h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: #ff00ff;
        }

        .process-content p {
            color: #ccc;
        }

        .trust-section {
            text-align: center;
            padding: 80px 20px;
            background: rgba(0, 245, 255, 0.05);
        }

        .trust-badge {
            display: inline-block;
            padding: 40px 60px;
            background: linear-gradient(135deg, rgba(0, 245, 255, 0.2), rgba(255, 0, 255, 0.2));
            border: 2px solid #00f5ff;
            border-radius: 20px;
            margin-top: 30px;
        }

        .trust-badge h3 {
            font-size: 3rem;
            color: #00ff88;
            margin-bottom: 15px;
        }

        .trust-badge p {
            font-size: 1.2rem;
            color: #ccc;
        }

        .checkmarks {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .check-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.1rem;
        }

        .check-icon {
            color: #00ff88;
            font-size: 1.5rem;
        }

        .price-table {
            max-width: 800px;
            margin: 40px auto;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .price-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .price-table th {
            background: linear-gradient(45deg, #00f5ff, #ff00ff);
            padding: 20px;
            font-size: 1.3rem;
            text-align: left;
        }

        .price-table td {
            padding: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .price-table tr:last-child td {
            border-bottom: none;
        }

        .price-highlight {
            font-size: 2rem;
            font-weight: bold;
            color: #00ff88;
        }

        .reviews {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .review-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            animation: fadeInUp 0.6s ease forwards;
            opacity: 0;
        }

        .review-card:nth-child(1) { animation-delay: 0.1s; }
        .review-card:nth-child(2) { animation-delay: 0.2s; }
        .review-card:nth-child(3) { animation-delay: 0.3s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
            from {
                transform: translateY(20px);
            }
        }

        .stars {
            color: #ffd700;
            font-size: 1.5rem;
            margin-bottom: 15px;
        }

        .review-text {
            color: #ccc;
            line-height: 1.6;
            font-style: italic;
            margin-bottom: 15px;
        }

        .reviewer {
            color: #00f5ff;
            font-weight: bold;
        }

        .cta-section {
            text-align: center;
            padding: 100px 20px;
            background: linear-gradient(135deg, rgba(0, 245, 255, 0.1), rgba(255, 0, 255, 0.1));
        }

        .cta-section h2 {
            font-size: clamp(2rem, 4vw, 3rem);
            margin-bottom: 20px;
            color: #00f5ff;
        }

        .cta-section p {
            font-size: 1.3rem;
            margin-bottom: 40px;
            color: #ccc;
        }

        .email-highlight {
            display: inline-block;
            padding: 15px 30px;
            background: rgba(0, 245, 255, 0.1);
            border: 2px solid #00f5ff;
            border-radius: 10px;
            margin-top: 20px;
            font-size: 1.2rem;
            color: #00f5ff;
        }

        footer {
            text-align: center;
            padding: 40px 20px;
            background: rgba(0, 0, 0, 0.3);
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        footer p {
            color: #888;
            margin-bottom: 10px;
        }

        .manual-badge {
            display: inline-block;
            padding: 10px 20px;
            background: linear-gradient(45deg, #ff00ff, #00f5ff);
            border-radius: 20px;
            margin: 20px 0;
            font-weight: bold;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @media (max-width: 768px) {
            .process-step {
                flex-direction: column;
                text-align: center;
            }

            .checkmarks {
                flex-direction: column;
                align-items: center;
            }

            .price-table {
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <div class="rocket"></div>
    <div class="rocket"></div>
    <div class="rocket"></div>
    <div class="rocket"></div>
    <div class="rocket"></div>
    <div class="rocket"></div>
    <div class="rocket"></div>

    <header>
        <div class="container">
            <div class="logo">🚀 Sites por R$15</div>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <h1>Criação de Sites por Apenas R$15</h1>
            <h2>Sites simples, rápidos e bonitos</h2>
            <p>Seu site no ar de forma rápida, simples e acessível. Visual moderno sem complicação. Menos custo, mais presença online.</p>
            <div class="manual-badge">✨ 100% Feito à Mão - Código HTML Completo</div>
            <a href="mailto:mantoantur@gmail.com?subject=Quero Criar Meu Site" class="btn">Quero Meu Site</a>
        </div>
    </section>

    <section class="section">
        <div class="container">
            <h2 class="section-title">O Que Eu Faço</h2>
            <div class="cards">
                <div class="card">
                    <div class="card-icon">💻</div>
                    <h3>Sites Institucionais</h3>
                    <p>Páginas profissionais para empresas, negócios e serviços. Cada projeto é feito com atenção ao visual e simplicidade.</p>
                </div>
                <div class="card">
                    <div class="card-icon">🎯</div>
                    <h3>Landing Pages</h3>
                    <p>Páginas de conversão focadas em resultados. Design pensado para atrair e converter visitantes em clientes.</p>
                </div>
                <div class="card">
                    <div class="card-icon">📱</div>
                    <h3>Portfólios Simples</h3>
                    <p>Mostre seu trabalho de forma elegante e moderna. Ideal para profissionais criativos e freelancers.</p>
                </div>
            </div>

            <div class="cards" style="margin-top: 50px;">
                <div class="card">
                    <div class="card-icon">⚡</div>
                    <h3>Tecnologias</h3>
                    <p><strong>HTML, CSS e JavaScript</strong> para criar sites responsivos, rápidos e com visual moderno. Código limpo e otimizado.</p>
                </div>
                <div class="card">
                    <div class="card-icon">🎨</div>
                    <h3>Design Moderno</h3>
                    <p>Layouts atuais, cores vibrantes e animações suaves. Seu site terá uma identidade visual profissional e atraente.</p>
                </div>
                <div class="card">
                    <div class="card-icon">✍️</div>
                    <h3>Código Manual</h3>
                    <p>Cada linha é escrita manualmente, sem geradores automáticos. Resultado: sites leves, rápidos e personalizados.</p>
                </div>
            </div>
        </div>
    </section>

    <section class="section" style="background: rgba(0, 0, 0, 0.2);">
        <div class="container">
            <h2 class="section-title">Como Funciona</h2>
            <div class="process">
                <div class="process-step">
                    <div class="process-number">01</div>
                    <div class="process-content">
                        <h3>Entre em Contato</h3>
                        <p>Envie um e-mail para mantoantur@gmail.com com sua ideia e o que você precisa no site.</p>
                    </div>
                </div>
                <div class="process-step">
                    <div class="process-number">02</div>
                    <div class="process-content">
                        <h3>Explique Sua Ideia</h3>
                        <p>Conte sobre seu projeto, cores preferidas, informações que devem aparecer e qualquer detalhe importante.</p>
                    </div>
                </div>
                <div class="process-step">
                    <div class="process-number">03</div>
                    <div class="process-content">
                        <h3>Realize o Pagamento</h3>
                        <p>Após alinharmos todos os detalhes, você faz o pagamento de R$15 para iniciar o desenvolvimento.</p>
                    </div>
                </div>
                <div class="process-step">
                    <div class="process-number">04</div>
                    <div class="process-content">
                        <h3>Desenvolvimento Manual</h3>
                        <p>Seu site é criado do zero com HTML, CSS e JavaScript, totalmente personalizado e otimizado.</p>
                    </div>
                </div>
                <div class="process-step">
                    <div class="process-number">05</div>
                    <div class="process-content">
                        <h3>Receba Seu Projeto</h3>
                        <p>O arquivo completo é enviado por e-mail. Você recebe o código pronto para usar onde quiser!</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="trust-section">
        <div class="container">
            <h2 class="section-title">Confiança 100%</h2>
            <div class="trust-badge">
                <h3>✓ Garantia de Qualidade</h3>
                <p>Transparência, comunicação clara e entrega conforme combinado</p>
            </div>
            <div class="checkmarks">
                <div class="check-item">
                    <span class="check-icon">✓</span>
                    <span>Código Limpo</span>
                </div>
                <div class="check-item">
                    <span class="check-icon">✓</span>
                    <span>Design Profissional</span>
                </div>
                <div class="check-item">
                    <span class="check-icon">✓</span>
                    <span>Entrega Rápida</span>
                </div>
                <div class="check-item">
                    <span class="check-icon">✓</span>
                    <span>Suporte Incluso</span>
                </div>
            </div>
        </div>
    </section>

    <section class="section">
        <div class="container">
            <h2 class="section-title">Tabela de Preços</h2>
            <p style="text-align: center; color: #ccc; margin-bottom: 30px;">Preço acessível para começar hoje mesmo sua presença online</p>
            <div class="price-table">
                <table>
                    <thead>
                        <tr>
                            <th>Serviço</th>
                            <th>Valor</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Criação de Site Simples</td>
                            <td><span class="price-highlight">R$15</span></td>
                        </tr>
                        <tr>
                            <td>Criação de App Simples</td>
                            <td>Consultar</td>
                        </tr>
                        <tr>
                            <td>Suporte Básico</td>
                            <td style="color: #00ff88; font-weight: bold;">Incluso ✓</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </section>

    <section class="section" style="background: rgba(0, 0, 0, 0.2);">
        <div class="container">
            <h2 class="section-title">O Que Dizem Nossos Clientes</h2>
            <div class="reviews">
                <div class="review-card">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="review-text">"Muito melhor do que eu esperava pelo valor. O site ficou bonito e funcionando perfeitamente. Recomendo!"</p>
                    <p class="reviewer">— Maria Silva</p>
                </div>
                <div class="review-card">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="review-text">"Entrega rápida e comunicação clara. O desenvolvedor entendeu exatamente o que eu precisava. Valeu cada centavo!"</p>
                    <p class="reviewer">— João Santos</p>
                </div>
                <div class="review-card">
                    <div class="stars">⭐⭐⭐⭐⭐</div>
                    <p class="review-text">"Visual simples e bonito. Código bem feito e fácil de entender. Serviço profissional por um preço inacreditável."</p>
                    <p class="reviewer">— Ana Paula</p>
                </div>
            </div>
        </div>
    </section>

    <section class="cta-section">
        <div class="container">
            <h2>Pronto para tirar sua ideia do papel?</h2>
            <p>Transforme sua presença digital com um site moderno, rápido e acessível</p>
            <a href="mailto:mantoantur@gmail.com?subject=Quero Criar Meu Site&body=Olá! Tenho interesse em criar um site." class="btn">Entrar em Contato</a>
            <div class="email-highlight">
                📧 mantoantur@gmail.com
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <p><strong>Sites por R$15</strong> - Criação profissional e acessível</p>
            <p>📧 E-mail: mantoantur@gmail.com</p>
            <p style="margin-top: 20px; font-size: 0.9rem;">© 2026 - Todos os direitos reservados. Serviço independente de desenvolvimento web.</p>
        </div>
    </footer>

    <script>
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }
            });
        });

        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.card, .process-step, .review-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
