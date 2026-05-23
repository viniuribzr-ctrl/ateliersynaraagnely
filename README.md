<html lang="pt-BR"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Atelier Synara Agnely | Catálogo Online</title>
    <!-- Fontes Originais -->
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700&amp;family=Montserrat:wght@300;400;600&amp;display=swap" rel="stylesheet">
    <style>
        :root {
            --black-purple: #0F021A;
            --purple: #5A189A;
            --dark-purple: #240046;
            --deep-purple: #1A0033;
            --lilac: #E0AAFF;
            --white: #FFFFFF;
            --dashed-border: 2px dashed var(--lilac);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }

        body {
            background-color: var(--deep-purple);
            color: var(--white);
            overflow-x: hidden;
        }

        .stitch-line {
            border-bottom: var(--dashed-border);
            height: 2px;
            width: 100%;
            opacity: 0.4;
            margin: 20px 0;
        }

        /* BANNER TOPO */
        .hero-header {
            position: relative;
            width: 100%;
            height: 440px; 
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            border-bottom: var(--dashed-border);
            background-color: var(--black-purple);
        }

        .carousel-track {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: 1;
        }

        .slide {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            opacity: 0;
            transform: translateX(100%);
            transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 1.2s ease-in-out;
        }

        .slide.active { opacity: 1; transform: translateX(0); }
        .slide.exit { opacity: 0; transform: translateX(-100%); }
        .slide img { width: 100%; height: 100%; object-fit: cover; }

        .hero-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: linear-gradient(to bottom, rgba(15, 2, 26, 0.3), rgba(36, 0, 70, 0.9));
            z-index: 2;
        }

        .header-content {
            position: relative;
            z-index: 3;
            text-align: center;
            padding: 20px;
            max-width: 800px;
            transition: opacity 0.4s ease, transform 0.4s ease;
        }

        body.scrolled .header-content {
            opacity: 0;
            transform: scale(0.8) translateY(-20px);
            pointer-events: none;
        }

        /* LOGO PRINCIPAL */
        .logo-container .logo-img {
            max-width: 420px;
            max-height: 180px; 
            object-fit: contain;
            filter: drop-shadow(0px 4px 15px rgba(0, 0, 0, 0.7));
        }

        .header-content h1 {
            font-family: 'Cinzel', serif;
            font-size: 3rem;
            letter-spacing: 5px;
            color: var(--white);
            text-shadow: 0px 4px 15px var(--black-purple);
        }

        .header-content p {
            font-size: 1rem;
            color: var(--lilac);
            text-transform: uppercase;
            letter-spacing: 4px;
            font-weight: 600;
            margin-top: 10px;
        }

        .carousel-arrow {
            position: absolute;
            top: 50%; transform: translateY(-50%);
            background: rgba(26, 0, 51, 0.6);
            border: 1px solid rgba(224, 170, 255, 0.3);
            color: white; padding: 14px 18px; cursor: pointer;
            border-radius: 50%; z-index: 4; font-weight: bold;
            transition: background 0.3s;
        }
        .carousel-arrow:hover { background: var(--purple); }
        .arrow-left { left: 20px; }
        .arrow-right { right: 20px; }

        /* BARRA DE ABAS FIXA (STICKY HEADER) */
        .sticky-wrapper {
            position: relative;
            width: 100%;
            z-index: 100;
        }

        .tabs-container {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            padding: 25px 40px;
            flex-wrap: wrap;
            background-color: var(--dark-purple);
            border-bottom: 1px solid rgba(224, 170, 255, 0.1);
            transition: all 0.4s ease;
        }

        body.scrolled .tabs-container {
            position: fixed;
            top: 0; left: 0; width: 100%;
            padding: 15px 40px;
            background-color: rgba(36, 0, 70, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 20px rgba(15, 2, 26, 0.5);
            justify-content: space-between;
            padding-left: 60px;
            padding-right: 60px;
        }

        .sticky-logo-area {
            display: none;
            align-items: center;
            order: 1;
        }

        body.scrolled .sticky-logo-area { display: flex; }

        /* SEGUNDA LOGO NO MENU FIXO */
        .sticky-mini-logo {
            max-width: 220px;
            max-height: 55px;
            object-fit: contain;
            filter: drop-shadow(0px 2px 8px rgba(0,0,0,0.5));
        }

        .sticky-text-logo {
            font-family: 'Cinzel', serif;
            font-size: 1.3rem;
            color: var(--white);
            letter-spacing: 2px;
        }

        .tabs-nav-box {
            display: flex; 
            gap: 12px; 
            flex-wrap: wrap; 
            justify-content: center;
            order: 2;
        }

        .tab-btn {
            background: rgba(90, 24, 154, 0.2);
            border: 2px solid var(--purple);
            color: var(--white);
            padding: 10px 24px;
            cursor: pointer;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            border-radius: 30px;
            font-weight: 600;
        }

        .tab-btn:hover, .tab-btn.active {
            background-color: var(--purple);
            border-color: var(--lilac);
            box-shadow: 0 0 15px rgba(224, 170, 255, 0.5);
        }

        .content-spacer { display: none; height: 90px; }
        body.scrolled .content-spacer { display: block; }

        /* Vitrine de Serviços */
        .catalog-container {
            max-width: 1200px;
            margin: 40px auto;
            padding: 0 20px;
        }

        .grid-services {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 35px;
        }

        .service-card {
            background-color: var(--dark-purple);
            border: 1px solid rgba(220, 170, 255, 0.15);
            border-radius: 12px;
            overflow: hidden;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(15, 2, 26, 0.4);
            cursor: pointer;
        }

        .service-card:hover {
            transform: translateY(-8px);
            border-color: var(--purple);
            box-shadow: 0 15px 30px rgba(90, 24, 154, 0.5);
        }

        .service-img {
            width: 100%;
            height: 260px;
            object-fit: cover;
            border-bottom: var(--dashed-border);
        }

        .service-info { padding: 22px; position: relative;}
        .service-info h3 { font-size: 1.3rem; margin-bottom: 12px; color: var(--lilac); }
        .service-info p { color: #e2d9eb; font-size: 0.9rem; line-height: 1.6; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
        .view-more-tag { font-size: 0.8rem; color: var(--lilac); font-weight: 600; margin-top: 15px; display: block; text-transform: uppercase; letter-spacing: 1px;}

        /* MODAL DE DETALHES DO SERVIÇO (30% MAIOR) */
        .detail-modal {
            display: none; position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(15, 2, 26, 0.96);
            backdrop-filter: blur(12px); z-index: 3000;
            justify-content: center; align-items: center; padding: 20px;
        }

        .detail-content {
            background-color: var(--dark-purple);
            border: 1px solid rgba(224, 170, 255, 0.3);
            max-width: 980px; width: 100%; /* Aumentado de 800px para 980px (Aprox. 30% maior) */
            border-radius: 16px; position: relative;
            overflow: hidden;
            box-shadow: 0 20px 50px rgba(0,0,0,0.8);
            display: grid;
            grid-template-columns: 1fr;
        }

        @media (min-width: 756px) {
            .detail-content { grid-template-columns: 1.1fr 0.9fr; } /* Proporção ligeiramente maior para o lado da foto */
        }

        .detail-media-side {
            position: relative;
            background: #000;
            height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        @media (min-width: 768px) { .detail-media-side { height: 100%; min-height: 540px; } } /* Altura aumentada para acompanhar a largura */

        .detail-slide {
            position: absolute; width: 100%; height: 100%;
            opacity: 0; transition: opacity 0.5s ease-in-out;
            object-fit: cover;
        }
        .detail-slide.active { opacity: 1; z-index: 5; }

        .detail-info-side {
            padding: 45px 35px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .detail-info-side h2 {
            font-family: 'Cinzel', serif;
            color: var(--lilac);
            font-size: 2rem; /* Aumentado proporcionalmente */
            margin-bottom: 18px;
            letter-spacing: 1px;
        }

        .detail-info-side p {
            color: #f1e6ff;
            font-size: 1rem; /* Aumentado para melhor leitura no popup grande */
            line-height: 1.8;
            margin-bottom: 30px;
        }

        .detail-close {
            position: absolute; top: 15px; right: 25px;
            font-size: 2.5rem; cursor: pointer; color: var(--lilac);
            z-index: 10; text-shadow: 0 2px 5px black;
            transition: color 0.2s;
        }
        .detail-close:hover { color: var(--white); }

        .detail-arrow {
            position: absolute; top: 50%; transform: translateY(-50%);
            background: rgba(15, 2, 26, 0.7); border: 1px solid rgba(224, 170, 255, 0.3);
            color: white; border-radius: 50%; width: 45px; height: 45px;
            cursor: pointer; z-index: 10; font-weight: bold; font-size: 1.4rem;
            display: flex; align-items: center; justify-content: center;
            transition: background 0.3s;
        }
        .detail-arrow:hover { background: var(--purple); }
        .detail-arrow-left { left: 20px; }
        .detail-arrow-right { right: 20px; }

        /* Rodapé */
        footer {
            background-color: var(--black-purple);
            padding: 50px 20px;
            margin-top: 80px;
            border-top: var(--dashed-border);
            text-align: center;
        }

        .footer-info {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 30px;
            margin: 30px 0;
        }

        .info-block h4 { color: var(--lilac); margin-bottom: 8px; text-transform: uppercase; }

        /* PAINEL E MODAIS ADMINISTRATIVOS */
        .admin-toggle {
            display: inline-flex; align-items: center; justify-content: center;
            background-color: transparent; color: rgba(224, 170, 255, 0.3); 
            border: 1px solid rgba(224, 170, 255, 0.1); width: 35px; height: 35px;
            border-radius: 50%; cursor: pointer; margin-top: 25px; transition: all 0.3s ease;
        }
        .admin-toggle:hover { transform: rotate(90deg); color: var(--lilac); background-color: var(--purple); box-shadow: 0 0 10px rgba(90, 24, 154, 0.6); }

        .admin-modal {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(26, 0, 51, 0.95); backdrop-filter: blur(8px); z-index: 2000;
            justify-content: center; align-items: center; padding: 20px;
        }

        .modal-content {
            background-color: var(--dark-purple); border: 2px solid var(--purple);
            padding: 30px; max-width: 950px; width: 100%; border-radius: 12px;
            position: relative; max-height: 90vh; overflow-y: auto;
        }

        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: var(--lilac); }
        .modal-content input, .modal-content textarea, .modal-content select { width: 100%; padding: 10px; margin: 8px 0 18px 0; background: var(--deep-purple); border: 1px solid var(--purple); color: white; border-radius: 6px; }
        .modal-content button { background-color: var(--purple); color: white; padding: 10px 20px; border: none; cursor: pointer; border-radius: 6px; font-weight: bold; width: 100%; }
        .modal-content button:hover { background-color: #7B2CBF; }
        .delete-btn { background-color: #b7094c !important; margin-top: 15px; }

        .admin-section-box { background: rgba(15,2,26,0.4); padding: 15px; border-radius: 8px; border: 1px solid rgba(224,170,255,0.1); margin-bottom: 20px; }
        .admin-carousel-list { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 10px; }
        .admin-carousel-item { position: relative; width: 80px; height: 60px; }
        .admin-carousel-item img { width:100%; height:100%; object-fit:cover; border-radius:4px; }
        .admin-carousel-item span { position: absolute; top:-5px; right:-5px; background:red; color:white; border-radius:50%; width:18px; height:18px; text-align:center; font-size:12px; cursor:pointer; line-height:16px; }

        @media (max-width: 768px) {
            .hero-header { height: 250px; }
            .header-content h1 { font-size: 2rem; }
            .logo-img { max-width: 260px; }
            body.scrolled .tabs-container { justify-content: center; padding-right: 20px; }
            body.scrolled .sticky-logo-area { display: none; }
            .footer-info { flex-direction: column; }
        }
    </style>
</head>
<body class="">

    <header class="hero-header" id="heroHeader">
        <div class="carousel-track" id="carouselView"><div class="slide active"><img src="https://images.unsplash.com/photo-1558603668-6570496b66f8?w=1200"></div><div class="slide exit"><img src="https://images.unsplash.com/photo-1520004481444-5f447e954831?w=1200"></div></div>
        <div class="hero-overlay"></div>
        
        <div class="header-content" id="headerContent">
            <div class="logo-container" id="logoView"><img src="https://i.postimg.co/N0MhXQvG/placeholder-logo.png" class="logo-img" alt="Logo"></div>
            <h1 id="titleView" style="display: none;">Atelier Synara Agnely</h1>
            <p>Sublimação • Bordado • Serigrafia • DTF</p>
        </div>

        <button class="carousel-arrow arrow-left" onclick="triggerManualSlide(-1)">❮</button>
        <button class="carousel-arrow arrow-right" onclick="triggerManualSlide(1)">❯</button>
    </header>

    <!-- STICKY HEADER -->
    <div class="sticky-wrapper" id="stickyNavbar">
        <nav class="tabs-container">
            <div class="sticky-logo-area" id="stickyLogoView"><img src="https://i.postimg.co/N0MhXQvG/placeholder-logo.png" class="sticky-mini-logo" alt="Logo Compacta"></div>
            <div class="tabs-nav-box" id="tabsNav"><button class="tab-btn active">Sublimação</button><button class="tab-btn ">Bordado</button><button class="tab-btn ">Serigrafia</button><button class="tab-btn ">teste</button></div>
        </nav>
    </div>
    <div class="content-spacer"></div>

    <!-- MODAL DETALHADO DO SERVIÇO (ABRINDO 30% MAIOR) -->
    <div id="serviceDetailModal" class="detail-modal">
        <div class="detail-content">
            <span class="detail-close" onclick="closeDetailModal()">×</span>
            
            <div class="detail-media-side">
                <div id="detailSlidesContainer" style="width:100%; height:100%;"></div>
                <button class="detail-arrow detail-arrow-left" onclick="changeDetailSlide(-1)">❮</button>
                <button class="detail-arrow detail-arrow-right" onclick="changeDetailSlide(1)">❯</button>
            </div>

            <div class="detail-info-side">
                <h2 id="detailTitle">Título do Trabalho</h2>
                <div style="border-bottom: 1px dashed rgba(224,170,255,0.2); margin-bottom: 15px;"></div>
                <p id="detailDesc">Descrição completa e técnica do trabalho aqui...</p>
                <button onclick="closeDetailModal()" style="background: transparent; border: 1px solid var(--lilac); color: white; padding: 12px; cursor: pointer; border-radius: 6px; font-weight: 600; transition: background 0.2s;" onmouseover="this.style.backgroundColor='rgba(224,170,255,0.1)'" onmouseout="this.style.backgroundColor='transparent'">Voltar ao Catálogo</button>
            </div>
        </div>
    </div>

    <!-- Modal de Login -->
    <div id="loginModal" class="admin-modal">
        <div class="modal-content" style="max-width: 380px;">
            <span class="close-modal" onclick="closeModals()">×</span>
            <h3 style="text-align: center; margin-bottom: 20px; color: var(--lilac);">Acesso Administrativo</h3>
            <label>Usuário:</label>
            <input type="text" id="usernameInput" placeholder="Usuário">
            <label>Senha:</label>
            <input type="password" id="passwordInput" placeholder="Senha">
            <button onclick="checkLogin()">Entrar no Painel</button>
        </div>
    </div>

    <!-- Modal Principal do Painel -->
    <div id="adminPanelModal" class="admin-modal">
        <div class="modal-content">
            <span class="close-modal" onclick="closeModals()">×</span>
            <h2 style="color: var(--lilac); margin-bottom: 15px;">Painel de Controle — Identidade &amp; Catálogo</h2>
            
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px;">
                <div class="admin-section-box">
                    <h3>Identidade Visual (Logos)</h3>
                    <label style="margin-top:10px; display:block;">1. URL da Logo Principal (Topo do Site):</label>
                    <input type="text" id="adminLogoUrl" placeholder="Link da logo principal">
                    <label style="margin-top:5px; display:block;">2. URL da Segunda Logo (Menu Fixo Rolável):</label>
                    <input type="text" id="adminStickyLogoUrl" placeholder="Link da logo horizontal/compacta para o menu">
                    <button onclick="updateLogos()">Salvar Identidade Visual</button>
                </div>

                <div class="admin-section-box">
                    <h3>Fotos de Fundo do Topo (Carrossel)</h3>
                    <label>Adicionar Novo Link de Foto Decorativa:</label>
                    <input type="text" id="adminCarouselUrl" placeholder="Cole o link da foto de fundo">
                    <button onclick="addCarouselImg()">Inserir no Carrossel</button>
                    <div class="admin-carousel-list" id="adminCarouselList"></div>
                </div>
            </div>

            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin-top: 10px;">
                <div class="admin-section-box">
                    <h3>Gerenciar Abas (Categorias)</h3>
                    <label>Nome da Nova Categoria:</label>
                    <input type="text" id="newTabName" placeholder="Ex: Uniformes Empresariais">
                    <button onclick="addTab()">Criar Aba</button>
                    <label style="margin-top: 25px; display: block; color: #ff85a2;">Remover Aba Ativa:</label>
                    <button class="delete-btn" onclick="deleteCurrentTab()">Excluir Aba Selecionada</button>
                </div>

                <div class="admin-section-box">
                    <h3>Postar Novo Trabalho Realizado</h3>
                    <label>Escolha a Categoria Alvo:</label>
                    <select id="itemTargetCategory"></select>

                    <label>Título do Serviço:</label>
                    <input type="text" id="itemTitle" placeholder="Ex: Camisas Polo Bordadas">
                    
                    <label>URLs das Fotos do Trabalho (Para colocar mais de uma, separe por vírgula):</label>
                    <textarea id="itemImg" rows="2" placeholder="http://linkdafoto1.com, http://linkdafoto2.com"></textarea>
                    
                    <label>Especificações Técnicas Completas:</label>
                    <textarea id="itemDesc" rows="3" placeholder="Detalhes técnicos relevantes para o cliente..."></textarea>
                    
                    <button onclick="addItem()">Publicar Serviço</button>
                </div>
            </div>
        </div>
    </div>

    <main class="catalog-container">
        <div class="grid-services" id="catalogGrid"><div class="service-card">
                        <img src="https://images.unsplash.com/photo-1576566588028-4147f3842f27?w=500" class="service-img" onclick="openDetailModal(1)">
                        <div class="service-info" onclick="openDetailModal(1)">
                            <h3>Abadá de Carnaval</h3>
                            <p>Sublimação total com toque super leve e secagem rápida. Ideal para blocos de grande porte com estampas vibrantes que não desbotam com o suor.</p>
                            <span class="view-more-tag">✨ Ver Detalhes &amp; Fotos</span>
                        </div>
                        
                    </div></div>
    </main>

    <footer>
        <div class="footer-content">
            <h2>Atelier Synara Agnely</h2>
            <div class="stitch-line"></div>
            <div class="footer-info">
                <div class="info-block">
                    <h4>📍 Endereço</h4>
                    <p>Rua Francisco Gomes de Vasconcelos, 751</p>
                    <p>Centro, Nova Floresta - PB</p>
                </div>
                <div class="info-block">
                    <h4>📞 Contatos</h4>
                    <p>(83) 99684-4269</p>
                    <p>contato@synaraagnely.com.br</p>
                </div>
            </div>
            <p style="font-size: 0.85rem; color: #7B2CBF; font-weight: 600;">© 2026 Atelier Synara Agnely. Portfólio Dinâmico Exclusivo.</p>
            <button class="admin-toggle" id="mainAdminBtn" onclick="openLoginModal()" title="Área Restrita">⚙️</button>
        </div>
    </footer>

    <script>
        const defaultData = {
            logo: "https://i.postimg.co/N0MhXQvG/placeholder-logo.png", 
            stickyLogo: "", 
            carousel: [
                "https://images.unsplash.com/photo-1558603668-6570496b66f8?w=1200",
                "https://images.unsplash.com/photo-1520004481444-5f447e954831?w=1200"
            ],
            categories: ["Sublimação", "Bordado", "Serigrafia"],
            items: [
                { id: 1, category: "Sublimação", title: "Abadá de Carnaval", desc: "Sublimação total com toque super leve e secagem rápida. Ideal para blocos de grande porte com estampas vibrantes que não desbotam com o suor.", images: ["https://images.unsplash.com/photo-1576566588028-4147f3842f27?w=500"] },
                { id: 2, category: "Bordado", title: "Enxoval Personalizado", desc: "Pontos fechados e brilhantes de alta costura em algodão nobre. Desenvolvido com matriz digitalizada sob medida para manter o relevo elegante.", images: ["https://images.unsplash.com/photo-1613521140210-b485398525e3?w=500", "https://images.unsplash.com/photo-1520004481444-5f447e954831?w=500"] }
            ]
        };

        let db = JSON.parse(localStorage.getItem('synara_portfolio_v7_db')) || defaultData;
        let activeTab = db.categories[0] || "";
        let currentSlideIndex = 0;
        let isLoggedIn = false;
        let carouselTimer = null;

        let currentDetailImages = [];
        let currentDetailImgIndex = 0;

        function saveData() {
            localStorage.setItem('synara_portfolio_v7_db', JSON.stringify(db));
            renderAll();
        }

        window.addEventListener('scroll', () => {
            const triggerPoint = document.getElementById('heroHeader').offsetHeight;
            if (window.scrollY >= triggerPoint) document.body.classList.add('scrolled');
            else document.body.classList.remove('scrolled');
        });

        function openLoginModal() {
            if (isLoggedIn) openAdminPanel();
            else document.getElementById('loginModal').style.display = 'flex';
        }
        
        function closeModals() {
            document.getElementById('loginModal').style.display = 'none';
            document.getElementById('adminPanelModal').style.display = 'none';
        }

        function checkLogin() {
            if (document.getElementById('usernameInput').value === 'synara' && document.getElementById('passwordInput').value === 'agnely') {
                isLoggedIn = true;
                document.getElementById('loginModal').style.display = 'none';
                document.getElementById('mainAdminBtn').innerText = "✔️";
                document.getElementById('mainAdminBtn').style.backgroundColor = "#2b9348";
                openAdminPanel();
            } else { alert("Acesso incorreto!"); }
        }

        function openAdminPanel() {
            document.getElementById('adminPanelModal').style.display = 'flex';
            document.getElementById('adminLogoUrl').value = db.logo || '';
            document.getElementById('adminStickyLogoUrl').value = db.stickyLogo || '';
            renderAdminSelectOptions();
            renderAdminCarouselThumbs();
        }

        function renderAdminSelectOptions() {
            const select = document.getElementById('itemTargetCategory');
            select.innerHTML = '';
            db.categories.forEach(cat => {
                const opt = document.createElement('option');
                opt.value = cat; opt.innerText = cat;
                select.appendChild(opt);
            });
        }

        function renderAll() {
            // Logos
            const logoContainer = document.getElementById('logoView');
            if(db.logo) {
                logoContainer.innerHTML = `<img src="${db.logo}" class="logo-img" alt="Logo">`;
                document.getElementById('titleView').style.display = "none";
            } else {
                logoContainer.innerHTML = "";
                document.getElementById('titleView').style.display = "block";
            }

            const stickyLogoContainer = document.getElementById('stickyLogoView');
            if(db.stickyLogo) stickyLogoContainer.innerHTML = `<img src="${db.stickyLogo}" class="sticky-mini-logo" alt="Logo Compacta">`;
            else if (db.logo) stickyLogoContainer.innerHTML = `<img src="${db.logo}" class="sticky-mini-logo" alt="Logo Compacta">`;
            else stickyLogoContainer.innerHTML = `<span class="sticky-text-logo">Atelier Synara Agnely</span>`;

            // Carrossel do Fundo
            const carouselView = document.getElementById('carouselView');
            carouselView.innerHTML = '';
            db.carousel.forEach((imgUrl, index) => {
                const slide = document.createElement('div');
                slide.className = `slide ${index === currentSlideIndex ? 'active' : ''}`;
                slide.innerHTML = `<img src="${imgUrl}">`;
                carouselView.appendChild(slide);
            });

            // Abas
            const tabsNav = document.getElementById('tabsNav');
            tabsNav.innerHTML = '';
            db.categories.forEach(cat => {
                const btn = document.createElement('button');
                btn.className = `tab-btn ${cat === activeTab ? 'active' : ''}`;
                btn.innerText = cat;
                btn.onclick = () => { activeTab = cat; renderAll(); };
                tabsNav.appendChild(btn);
            });

            // Grade de Trabalhos
            const grid = document.getElementById('catalogGrid');
            grid.innerHTML = '';
            const filtered = db.items.filter(item => item.category === activeTab);
            
            if(filtered.length === 0) {
                grid.innerHTML = `<p style="grid-column: 1/-1; text-align: center; color: var(--lilac); padding: 40px; font-style: italic;">Nenhum item cadastrado aqui.</p>`;
            } else {
                filtered.forEach(item => {
                    const card = document.createElement('div');
                    card.className = 'service-card';
                    const coverImg = (item.images && item.images.length > 0) ? item.images[0] : 'https://placehold.co/600x400/240046/e0aaff?text=Sem+Foto';
                    
                    card.innerHTML = `
                        <img src="${coverImg}" class="service-img" onclick="openDetailModal(${item.id})">
                        <div class="service-info" onclick="openDetailModal(${item.id})">
                            <h3>${item.title}</h3>
                            <p>${item.desc}</p>
                            <span class="view-more-tag">✨ Ver Detalhes & Fotos</span>
                        </div>
                        ${isLoggedIn ? `<div style="padding: 0 22px 22px 22px;"><button class="delete-btn" style="width:100%" onclick="deleteItem(${item.id}); event.stopPropagation();">🗑️ Excluir Post</button></div>` : ''}
                    `;
                    grid.appendChild(card);
                });
            }
        }

        // CONTROLADORES DA JANELA DE DETALHES
        function openDetailModal(id) {
            const item = db.items.find(i => i.id === id);
            if (!item) return;

            document.getElementById('detailTitle').innerText = item.title;
            document.getElementById('detailDesc').innerText = item.desc;
            
            currentDetailImages = item.images && item.images.length > 0 ? item.images : ['https://placehold.co/600x400/240046/e0aaff?text=Sem+Foto'];
            currentDetailImgIndex = 0;

            renderDetailSlides();
            document.getElementById('serviceDetailModal').style.display = 'flex';
        }

        function renderDetailSlides() {
            const container = document.getElementById('detailSlidesContainer');
            container.innerHTML = '';
            currentDetailImages.forEach((url, index) => {
                const img = document.createElement('img');
                img.src = url;
                img.className = `detail-slide ${index === currentDetailImgIndex ? 'active' : ''}`;
                container.appendChild(img);
            });
            
            const arrows = document.querySelectorAll('.detail-arrow');
            arrows.forEach(arr => arr.style.display = currentDetailImages.length > 1 ? 'flex' : 'none');
        }

        function changeDetailSlide(direction) {
            currentDetailImgIndex = (currentDetailImgIndex + direction + currentDetailImages.length) % currentDetailImages.length;
            renderDetailSlides();
        }

        function closeDetailModal() {
            document.getElementById('serviceDetailModal').style.display = 'none';
        }

        // CARROSSEL DO TOPO
        function advanceSlide(direction = 1) {
            const slides = document.querySelectorAll('.slide');
            if (slides.length <= 1) return;
            const oldIndex = currentSlideIndex;
            currentSlideIndex = (currentSlideIndex + direction + slides.length) % slides.length;

            slides.forEach((slide, idx) => {
                slide.classList.remove('active', 'exit');
                if (idx === oldIndex) slide.classList.add('exit');
                else if (idx === currentSlideIndex) slide.classList.add('active');
            });
        }
        function startAutoplay() { stopAutoplay(); carouselTimer = setInterval(() => { advanceSlide(1); }, 5000); }
        function stopAutoplay() { if (carouselTimer) clearInterval(carouselTimer); }
        function triggerManualSlide(direction) { stopAutoplay(); advanceSlide(direction); startAutoplay(); }

        // GERENCIAMENTO DO PAINEL ADMIN
        function updateLogos() {
            db.logo = document.getElementById('adminLogoUrl').value.trim();
            db.stickyLogo = document.getElementById('adminStickyLogoUrl').value.trim();
            saveData();
            alert("Identidade salva!");
        }

        function addCarouselImg() {
            const url = document.getElementById('adminCarouselUrl').value.trim();
            if(url) {
                db.carousel.push(url);
                document.getElementById('adminCarouselUrl').value = '';
                saveData();
                renderAdminCarouselThumbs();
            }
        }

        function removeCarouselImg(index) {
            db.carousel.splice(index, 1);
            currentSlideIndex = 0;
            saveData();
            renderAdminCarouselThumbs();
        }

        function renderAdminCarouselThumbs() {
            const container = document.getElementById('adminCarouselList');
            container.innerHTML = '';
            db.carousel.forEach((url, i) => {
                const div = document.createElement('div');
                div.className = 'admin-carousel-item';
                div.innerHTML = `<img src="${url}"><span onclick="removeCarouselImg(${i})">&times;</span>`;
                container.appendChild(div);
            });
        }

        function addTab() {
            const name = document.getElementById('newTabName').value.trim();
            if(name && !db.categories.includes(name)) {
                db.categories.push(name); activeTab = name;
                document.getElementById('newTabName').value = '';
                saveData(); renderAdminSelectOptions();
            }
        }

        function deleteCurrentTab() {
            if(confirm(`Apagar a categoria "${activeTab}"?`)) {
                db.items = db.items.filter(item => item.category !== activeTab);
                db.categories = db.categories.filter(cat => cat !== activeTab);
                activeTab = db.categories[0] || "";
                saveData(); renderAdminSelectOptions();
            }
        }

        function addItem() {
            const chosenCategory = document.getElementById('itemTargetCategory').value;
            const title = document.getElementById('itemTitle').value.trim();
            const rawImgUrls = document.getElementById('itemImg').value.trim();
            const desc = document.getElementById('itemDesc').value.trim();

            if(chosenCategory && title && rawImgUrls && desc) {
                const imagesArray = rawImgUrls.split(',').map(url => url.trim()).filter(url => url.length > 0);

                db.items.push({ id: Date.now(), category: chosenCategory, title, desc, images: imagesArray });
                
                document.getElementById('itemTitle').value = '';
                document.getElementById('itemImg').value = '';
                document.getElementById('itemDesc').value = '';
                activeTab = chosenCategory;
                saveData();
                alert("Serviço publicado com sucesso com múltiplas mídias!");
            } else { alert("Preencha todos os campos."); }
        }

        function deleteItem(id) {
            if(confirm("Deseja excluir este item?")) {
                db.items = db.items.filter(item => item.id !== id);
                saveData();
            }
        }

        renderAll();
        startAutoplay();
    </script>


</body></html>
