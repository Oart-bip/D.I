LINK DA APLICAÇÃO: https://visionary-zabaione-e37963.netlify.app

CÓDIGO:

HTML -------------------------------
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <!-- Configurações básicas da página -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bebidas Premium - E-commerce</title>
    <meta name="description" content="Loja online de bebidas premium com variedade de vinhos, cervejas e destilados">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Cabeçalho principal com navegação -->
    <header>
        <nav>
            <div class="nav-container">
                <!-- Logo da loja -->
                <div class="logo">
                    <h1>Bebidas Premium</h1>
                </div>             
                <!-- Menu de navegação principal -->
                <ul class="nav-menu">
                    <li><a href="#home">Início</a></li>
                    <li><a href="#produtos">Produtos</a></li>
                    <li><a href="#dashboard">Dashboard</a></li>
                    <li><a href="#admin">Admin</a></li>
                </ul>            
                <!-- Botões de ação do usuário (carrinho e perfil) -->
                <div class="nav-actions">
                    <button class="cart-btn" aria-label="Carrinho de compras">
                        <span class="cart-icon">🛒</span>
                        <span class="cart-count">0</span> <!-- Contador de itens no carrinho -->
                    </button>
                    <button class="user-btn" aria-label="Área do usuário">👤</button>
                </div>
            </div>
        </nav>
    </header>
    <main>
        <!-- Seção hero - banner principal da página -->
        <section id="home" class="hero-section">
            <div class="hero-content">
                <h2>Bebidas Premium para Todos os Momentos</h2>
                <p>Descubra nossa seleção exclusiva de vinhos, cervejas artesanais e destilados premium</p>
                <button class="cta-button">Ver Produtos</button> <!-- Botão de chamada para ação -->
            </div>
            <div class="hero-image">
                <img src="bebidas.png" alt="Coleção de bebidas premium" class="hero-img">
            </div>
        </section>
        <!-- Seção de produtos com filtros -->
        <section id="produtos" class="products-section">
            <div class="section-header">
                <h2>Nossos Produtos</h2>      
                <!-- Filtros para buscar produtos -->
                <div class="filters">
                    <label for="category-filter">Categoria:</label>
                    <select id="category-filter" name="category">
                        <option value="">Todas</option>
                        <option value="vinho">Vinhos</option>
                        <option value="cerveja">Cervejas</option>
                        <option value="destilado">Destilados</option>
                        <option value="nao-alcoolico">Não Alcoólicos</option>
                    </select>        
                    <label for="price-filter">Preço:</label>
                    <select id="price-filter" name="price">
                        <option value="">Todos</option>
                        <option value="0-50">R$ 0 - 50</option>
                        <option value="50-100">R$ 50 - 100</option>
                        <option value="100-200">R$ 100 - 200</option>
                        <option value="200+">R$ 200+</option>
                    </select>         
                    <button id="search-btn" type="button">Buscar</button>
                </div>
            </div>           
            <!-- Grid onde os produtos serão exibidos dinamicamente -->
            <div class="products-grid" id="products-grid">
            </div>
        </section>
        <!-- Dashboard para visualizar estatísticas do estoque -->
        <section id="dashboard" class="dashboard-section">
            <div class="dashboard-header">
                <h2>Dashboard de Estoque</h2>
                <div class="dashboard-controls">
                    <button id="refresh-dashboard">Atualizar</button>
                    <button id="export-report">Exportar Relatório</button>
                </div>
            </div>     
            <div class="dashboard-grid">
                <!-- Card com resumo geral do estoque -->
                <div class="dashboard-card">
                    <h3>Resumo do Estoque</h3>
                    <div class="stats-grid">
                        <div class="stat-item">
                            <span class="stat-label">Total de Produtos</span>
                            <span class="stat-value" id="total-products">0</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Produtos em Estoque</span>
                            <span class="stat-value" id="in-stock">0</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Produtos Esgotados</span>
                            <span class="stat-value" id="out-of-stock">0</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-label">Valor Total do Estoque</span>
                            <span class="stat-value" id="total-value">R$ 0,00</span>
                        </div>
                    </div>
                </div>        
                <!-- Card com gráfico de produtos por categoria -->
                <div class="dashboard-card">
                    <h3>Produtos por Categoria</h3>
                    <div class="chart-container">
                        <canvas id="category-chart" width="400" height="200"></canvas>
                    </div>
                </div>        
                <!-- Card com lista de produtos com estoque baixo -->
                <div class="dashboard-card">
                    <h3>Produtos com Estoque Baixo</h3>
                    <div class="low-stock-list" id="low-stock-list">
                    </div>
                </div>          
                <!-- Card com gráfico de vendas mensais -->
                <div class="dashboard-card">
                    <h3>Vendas por Mês</h3>
                    <div class="chart-container">
                        <canvas id="sales-chart" width="400" height="200"></canvas>
                    </div>
                </div>
            </div>
        </section>
        <!-- Seção administrativa para gerenciar produtos -->
        <section id="admin" class="admin-section">
            <div class="admin-header">
                <h2>Gerenciamento de Produtos</h2>
                <button id="add-product-btn" class="primary-btn">Adicionar Produto</button>
            </div>           
            <div class="admin-content">
                <!-- Tabela com todos os produtos para administração -->
                <div class="admin-table-container">
                    <table class="admin-table" id="admin-table">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Imagem</th>
                                <th>Nome</th>
                                <th>Categoria</th>
                                <th>Preço</th>
                                <th>Estoque</th>
                                <th>Status</th>
                                <th>Ações</th> <!-- Botões para editar/excluir -->
                            </tr>
                        </thead>
                        <tbody id="admin-table-body">
                        </tbody>
                    </table>
                </div>
            </div>
        </section>
    </main>
    <!-- Modal para adicionar/editar produtos -->
    <div id="product-modal" class="modal" aria-hidden="true" role="dialog" aria-labelledby="modal-title">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modal-title">Adicionar Produto</h3>
                <button class="modal-close" aria-label="Fechar modal">&times;</button>
            </div>        
            <!-- Formulário para dados do produto -->
            <form id="product-form" class="modal-body">
                <div class="form-group">
                    <label for="product-name">Nome do Produto *</label>
                    <input type="text" id="product-name" name="name" required aria-describedby="name-error">
                    <span class="error-message" id="name-error"></span> <!-- Mensagem de erro -->
                </div>              
                <div class="form-group">
                    <label for="product-category">Categoria *</label>
                    <select id="product-category" name="category" required aria-describedby="category-error">
                        <option value="">Selecione uma categoria</option>
                        <option value="vinho">Vinho</option>
                        <option value="cerveja">Cerveja</option>
                        <option value="destilado">Destilado</option>
                        <option value="nao-alcoolico">Não Alcoólico</option>
                    </select>
                    <span class="error-message" id="category-error"></span>
                </div>               
                <div class="form-group">
                    <label for="product-price">Preço *</label>
                    <input type="number" id="product-price" name="price" step="0.01" min="0" required aria-describedby="price-error">
                    <span class="error-message" id="price-error"></span>
                </div>               
                <div class="form-group">
                    <label for="product-stock">Quantidade em Estoque *</label>
                    <input type="number" id="product-stock" name="stock" min="0" required aria-describedby="stock-error">
                    <span class="error-message" id="stock-error"></span>
                </div>                
                <div class="form-group">
                    <label for="product-description">Descrição</label>
                    <textarea id="product-description" name="description" rows="4" aria-describedby="description-help"></textarea>
                    <span class="help-text" id="description-help">Opcional: Descreva as características do produto</span>
                </div>                
                <div class="form-group">
                    <label for="product-image">URL da Imagem</label>
                    <input type="url" id="product-image" name="image" aria-describedby="image-help">
                    <span class="help-text" id="image-help">Opcional: Cole o link da imagem do produto</span>
                </div>                
                <div class="form-group">
                    <label for="product-alcohol">Teor Alcoólico (%)</label>
                    <input type="number" id="product-alcohol" name="alcohol" step="0.1" min="0" max="100">
                </div>               
                <div class="form-group">
                    <label for="product-volume">Volume (ml)</label>
                    <input type="number" id="product-volume" name="volume" min="1">
                </div>
            </form>            
            <!-- Botões de ação do modal -->
            <div class="modal-footer">
                <button type="button" id="cancel-btn" class="secondary-btn">Cancelar</button>
                <button type="submit" form="product-form" id="save-btn" class="primary-btn">Salvar</button>
            </div>
        </div>
    </div>
    <!-- Modal de confirmação para ações importantes -->
    <div id="confirm-modal" class="modal" aria-hidden="true" role="dialog">
        <div class="modal-content confirm-modal">
            <div class="modal-header">
                <h3>Confirmar Ação</h3>
            </div>
            <div class="modal-body">
                <p id="confirm-message">Tem certeza que deseja realizar esta ação?</p>
            </div>
            <div class="modal-footer">
                <button type="button" id="confirm-cancel" class="secondary-btn">Cancelar</button>
                <button type="button" id="confirm-ok" class="danger-btn">Confirmar</button>
            </div>
        </div>
    </div>
    <!-- Sidebar do carrinho de compras -->
    <div id="cart-sidebar" class="cart-sidebar" aria-hidden="true">
        <div class="cart-header">
            <h3>Carrinho de Compras</h3>
            <button class="cart-close" aria-label="Fechar carrinho">&times;</button>
        </div>
        <div class="cart-body" id="cart-items">
            <!-- Itens do carrinho serão inseridos aqui dinamicamente -->
        </div>
        <div class="cart-footer">
            <div class="cart-total">
                <strong>Total: <span id="cart-total">R$ 0,00</span></strong>
            </div>
            <button class="checkout-btn" id="checkout-btn">Finalizar Compra</button>
        </div>
    </div>
    <!-- Overlay para modais (fundo escuro) -->
    <div id="modal-overlay" class="modal-overlay" aria-hidden="true"></div>
    <!-- Container para notificações toast -->
    <div id="toast-container" class="toast-container" aria-live="polite"></div>
    <!-- Spinner de carregamento -->
    <div id="loading-spinner" class="loading-spinner" aria-hidden="true">
        <div class="spinner"></div>
        <p>Carregando...</p>
    </div>
    <!-- Rodapé da página -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h4>Bebidas Premium</h4>
                <p>Sua loja online de bebidas premium com qualidade e variedade.</p>
            </div>
            <div class="footer-section">
                <h4>Contato</h4>
                <p>Email: contato@bebidaspremium.com</p>
                <p>Telefone: (11) 9999-9999</p>
            </div>
            <div class="footer-section">
                <h4>Sobre</h4>
                <p>Campo Real 2025</p>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2024 Bebidas Premium. Todos os direitos reservados.</p>
        </div>
    </footer>
    <!-- Script JavaScript principal -->
    <script src="script.js"></script>
</body>
</html>

CSS ----------------------------------------------

/* Reset básico - remove margens, paddings e define box-sizing para todos os elementos */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Estilos base do corpo da página */
body {
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f8f9fa;
}

/* Container principal da navegação */
.nav-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
}

/* Cabeçalho com gradiente e posição fixa */
header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    position: sticky; /* Fica fixo no topo ao rolar */
    top: 0;
    z-index: 1000;
}

/* Logo do site */
.logo h1 {
    font-size: 1.8rem;
    font-weight: 700;
}

/* Menu de navegação horizontal */
.nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
}

/* Links do menu com efeito hover */
.nav-menu a {
    color: white;
    text-decoration: none;
    transition: color 0.3s ease;
    font-weight: 500;
}

.nav-menu a:hover {
    color: #ffd700; /* Muda para dourado no hover */
}

/* Área de ações do usuário (carrinho, login) */
.nav-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
}

/* Botões do carrinho e usuário com efeito glassmorphism */
.cart-btn, .user-btn {
    background: rgba(255,255,255,0.2);
    border: none;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

/* Efeito hover nos botões com elevação */
.cart-btn:hover, .user-btn:hover {
    background: rgba(255,255,255,0.3);
    transform: translateY(-2px);
}

/* Contador de itens no carrinho */
.cart-count {
    background: #ff4757;
    color: white;
    border-radius: 50%;
    padding: 0.2rem 0.5rem;
    font-size: 0.8rem;
    font-weight: bold;
}

/* Seção hero principal com imagem de fundo */
.hero-section {
    background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('hero-bg.jpg');
    background-size: cover;
    background-position: center;
    padding: 5rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1200px;
    margin: 0 auto;
    color: white;
    min-height: 60vh;
}

/* Conteúdo de texto da seção hero */
.hero-content {
    flex: 1;
    max-width: 600px;
}

/* Título principal da hero */
.hero-content h2 {
    font-size: 3rem;
    margin-bottom: 1rem;
    font-weight: 700;
}

/* Parágrafo da hero */
.hero-content p {
    font-size: 1.2rem;
    margin-bottom: 2rem;
    opacity: 0.9;
}

/* Botão de call-to-action com gradiente */
.cta-button {
    background: linear-gradient(135deg, #ff6b6b, #ee5a24);
    color: white;
    border: none;
    padding: 1rem 2rem;
    font-size: 1.1rem;
    border-radius: 50px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-weight: 600;
}

/* Efeito hover no CTA com sombra */
.cta-button:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}

/* Container da imagem na hero */
.hero-image {
    flex: 1;
    text-align: center;
}

/* Imagem da hero responsiva */
.hero-img {
    max-width: 100%;
    height: auto;
    border-radius: 15px;
}

/* Seção de produtos */
.products-section {
    padding: 4rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

/* Cabeçalho das seções */
.section-header {
    margin-bottom: 3rem;
    text-align: center;
}

.section-header h2 {
    font-size: 2.5rem;
    margin-bottom: 2rem;
    color: #2c3e50;
}

/* Filtros de produtos com card branco */
.filters {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
    background: white;
    padding: 1.5rem;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

/* Labels dos filtros */
.filters label {
    font-weight: 600;
    color: #2c3e50;
}

/* Campos select dos filtros */
.filters select {
    padding: 0.5rem;
    border: 2px solid #e9ecef;
    border-radius: 8px;
    font-size: 1rem;
    transition: border-color 0.3s ease;
}

/* Efeito focus nos selects */
.filters select:focus {
    outline: none;
    border-color: #667eea;
}

/* Botão de busca */
#search-btn {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    border: none;
    padding: 0.5rem 1.5rem;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 600;
    transition: all 0.3s ease;
}

#search-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

/* Grid responsivo de produtos */
.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
}

/* Card individual de produto */
.product-card {
    background: white;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    transition: all 0.3s ease;
    cursor: pointer;
}

/* Efeito hover no card com elevação */
.product-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.2);
}

/* Container da imagem do produto */
.product-image {
    width: 100%;
    height: 200px;
    background: #f8f9fa;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #adb5bd;
    font-size: 1.2rem;
}

/* Imagem do produto */
.product-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

/* Informações do produto */
.product-info {
    padding: 1.5rem;
}

/* Nome do produto */
.product-name {
    font-size: 1.2rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: #2c3e50;
}

/* Categoria do produto */
.product-category {
    color: #667eea;
    font-size: 0.9rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    text-transform: uppercase;
}

/* Preço do produto */
.product-price {
    font-size: 1.5rem;
    font-weight: 700;
    color: #27ae60;
    margin-bottom: 1rem;
}

/* Container de ações do produto */
.product-actions {
    display: flex;
    gap: 0.5rem;
}

/* Classe base para botões */
.btn {
    padding: 0.5rem 1rem;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 600;
    transition: all 0.3s ease;
    text-decoration: none;
    display: inline-block;
    text-align: center;
}

/* Variações de cores dos botões */
.primary-btn {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
}

.secondary-btn {
    background: #6c757d;
    color: white;
}

.danger-btn {
    background: #dc3545;
    color: white;
}

.success-btn {
    background: #28a745;
    color: white;
}

/* Efeito hover universal dos botões */
.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

/* Seção do dashboard administrativo */
.dashboard-section {
    padding: 4rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
    background: white;
    margin-top: 2rem;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

/* Cabeçalho do dashboard */
.dashboard-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
    flex-wrap: wrap;
    gap: 1rem;
}

.dashboard-header h2 {
    font-size: 2.5rem;
    color: #2c3e50;
}

/* Controles do dashboard */
.dashboard-controls {
    display: flex;
    gap: 1rem;
}

/* Grid do dashboard */
.dashboard-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

/* Cards do dashboard */
.dashboard-card {
    background: #f8f9fa;
    padding: 2rem;
    border-radius: 15px;
    border-left: 5px solid #667eea; /* Borda lateral colorida */
}

.dashboard-card h3 {
    margin-bottom: 1.5rem;
    color: #2c3e50;
    font-size: 1.3rem;
}

/* Grid de estatísticas */
.stats-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
}

/* Item individual de estatística */
.stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 1rem;
    background: white;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

/* Label da estatística */
.stat-label {
    font-size: 0.9rem;
    color: #6c757d;
    margin-bottom: 0.5rem;
}

/* Valor da estatística */
.stat-value {
    font-size: 1.5rem;
    font-weight: 700;
    color: #2c3e50;
}

/* Container de gráficos */
.chart-container {
    background: white;
    padding: 1rem;
    border-radius: 10px;
    height: 250px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Lista de produtos com estoque baixo */
.low-stock-list {
    background: white;
    border-radius: 10px;
    max-height: 250px;
    overflow-y: auto;
}

/* Item da lista de estoque baixo */
.low-stock-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    border-bottom: 1px solid #e9ecef;
}

.low-stock-item:last-child {
    border-bottom: none;
}

/* Seção administrativa */
.admin-section {
    padding: 4rem 2rem;
    max-width: 1200px;
    margin: 2rem auto;
    background: white;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

/* Cabeçalho da seção admin */
.admin-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
    flex-wrap: wrap;
    gap: 1rem;
}

.admin-header h2 {
    font-size: 2.5rem;
    color: #2c3e50;
}

/* Container da tabela admin com scroll horizontal */
.admin-table-container {
    overflow-x: auto;
}

/* Tabela administrativa */
.admin-table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

/* Células da tabela */
.admin-table th,
.admin-table td {
    padding: 1rem;
    text-align: left;
    border-bottom: 1px solid #e9ecef;
}

/* Cabeçalho da tabela com gradiente */
.admin-table th {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
    font-weight: 600;
}

/* Efeito hover nas linhas da tabela */
.admin-table tr:hover {
    background: #f8f9fa;
}

/* Imagem pequena do produto na tabela */
.product-image-small {
    width: 60px;
    height: 60px;
    object-fit: cover;
    border-radius: 8px;
}

/* Badge de status base */
.status-badge {
    padding: 0.3rem 0.8rem;
    border-radius: 20px;
    font-size: 0.8rem;
    font-weight: 600;
    text-transform: uppercase;
}

/* Variações de status por cor */
.status-in-stock {
    background: #d4edda;
    color: #155724;
}

.status-low-stock {
    background: #fff3cd;
    color: #856404;
}

.status-out-of-stock {
    background: #f8d7da;
    color: #721c24;
}

/* Container de botões de ação */
.action-buttons {
    display: flex;
    gap: 0.5rem;
}

/* Botão pequeno para tabelas */
.btn-small {
    padding: 0.3rem 0.8rem;
    font-size: 0.8rem;
}

/* Modal overlay fixo */
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    display: none;
    justify-content: center;
    align-items: center;
    z-index: 2000;
}

/* Modal ativo */
.modal.active {
    display: flex;
}

/* Conteúdo do modal */
.modal-content {
    background: white;
    border-radius: 15px;
    max-width: 600px;
    width: 90%;
    max-height: 90vh;
    overflow-y: auto;
    animation: modalSlideIn 0.3s ease;
}

/* Animação de entrada do modal */
@keyframes modalSlideIn {
    from {
        transform: translateY(-50px);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

/* Cabeçalho do modal */
.modal-header {
    padding: 1.5rem;
    border-bottom: 1px solid #e9ecef;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.modal-header h3 {
    color: #2c3e50;
    font-size: 1.5rem;
}

/* Botão de fechar modal */
.modal-close {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    color: #6c757d;
    padding: 0.5rem;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal-close:hover {
    background: #f8f9fa;
}

/* Corpo do modal */
.modal-body {
    padding: 1.5rem;
}

/* Rodapé do modal */
.modal-footer {
    padding: 1.5rem;
    border-top: 1px solid #e9ecef;
    display: flex;
    justify-content: flex-end;
    gap: 1rem;
}

/* Grupo de campos do formulário */
.form-group {
    margin-bottom: 1.5rem;
}

/* Label do formulário */
.form-group label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: 600;
    color: #2c3e50;
}

/* Campos de entrada do formulário */
.form-group input,
.form-group select,
.form-group textarea {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid #e9ecef;
    border-radius: 8px;
    font-size: 1rem;
    transition: border-color 0.3s ease;
}

/* Efeito focus nos campos */
.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
    outline: none;
    border-color: #667eea;
}

/* Mensagem de erro */
.error-message {
    color: #dc3545;
    font-size: 0.9rem;
    margin-top: 0.5rem;
    display: block;
}

/* Texto de ajuda */
.help-text {
    color: #6c757d;
    font-size: 0.9rem;
    margin-top: 0.5rem;
    display: block;
}

/* Modal de confirmação menor */
.confirm-modal .modal-content {
    max-width: 400px;
}

/* Sidebar do carrinho fixo na lateral */
.cart-sidebar {
    position: fixed;
    top: 0;
    right: -400px; /* Inicialmente escondido */
    width: 400px;
    height: 100%;
    background: white;
    box-shadow: -5px 0 15px rgba(0,0,0,0.1);
    transition: right 0.3s ease;
    z-index: 2500;
    display: flex;
    flex-direction: column;
}

/* Sidebar ativo */
.cart-sidebar.active {
    right: 0;
}

/* Cabeçalho do carrinho */
.cart-header {
    padding: 1.5rem;
    border-bottom: 1px solid #e9ecef;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: white;
}

/* Botão de fechar carrinho */
.cart-close {
    background: none;
    border: none;
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.cart-close:hover {
    background: rgba(255,255,255,0.2);
}

/* Corpo do carrinho com scroll */
.cart-body {
    flex: 1;
    padding: 1rem;
    overflow-y: auto;
}

/* Item individual do carrinho */
.cart-item {
    display: flex;
    gap: 1rem;
    padding: 1rem;
    border-bottom: 1px solid #e9ecef;
    align-items: center;
}

/* Imagem do item no carrinho */
.cart-item-image {
    width: 60px;
    height: 60px;
    background: #f8f9fa;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Informações do item no carrinho */
.cart-item-info {
    flex: 1;
}

/* Nome do item no carrinho */
.cart-item-name {
    font-weight: 600;
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

/* Preço do item no carrinho */
.cart-item-price {
    color: #27ae60;
    font-weight: 600;
}

/* Controles de quantidade */
.cart-item-controls {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-top: 0.5rem;
}

/* Botões de quantidade circular */
.quantity-btn {
    background: #667eea;
    color: white;
    border: none;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
}

/* Rodapé do carrinho */
.cart-footer {
    padding: 1.5rem;
    border-top: 1px solid #e9ecef;
    background: #f8f9fa;
}

/* Total do carrinho */
.cart-total {
    margin-bottom: 1rem;
    text-align: center;
    font-size: 1.2rem;
}

/* Botão de checkout */
.checkout-btn {
    width: 100%;
    padding: 1rem;
    background: linear-gradient(135deg, #28a745, #20c997);
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
}

.checkout-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}

/* Overlay para modal */
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 1500;
    display: none;
}

.modal-overlay.active {
    display: block;
}

/* Container de notificações toast */
.toast-container {
    position: fixed;
    top: 100px;
    right: 20px;
    z-index: 3000;
}

/* Notificação toast */
.toast {
    background: white;
    padding: 1rem 1.5rem;
    border-radius: 8px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    margin-bottom: 1rem;
    border-left: 4px solid #28a745; /* Borda colorida por tipo */
    animation: toastSlideIn 0.3s ease;
}

/* Variações de toast por tipo */
.toast.error {
    border-left-color: #dc3545;
}

.toast.warning {
    border-left-color: #ffc107;
}

/* Animação de entrada do toast */
@keyframes toastSlideIn {
    from {
        transform: translateX(100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

/* Loading spinner de tela cheia */
.loading-spinner {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255,255,255,0.8);
    display: none;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 3500;
}

.loading-spinner.active {
    display: flex;
}

/* Spinner animado */
.spinner {
    width: 50px;
    height: 50px;
    border: 4px solid #e9ecef;
    border-top: 4px solid #667eea;
    border-radius: 50%;
    animation: spin 1s linear infinite;
    margin-bottom: 1rem;
}

/* Animação de rotação do spinner */
@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Rodapé da página */
footer {
    background: #2c3e50;
    color: white;
    padding: 3rem 2rem 1rem;
    margin-top: 4rem;
}

/* Conteúdo do rodapé em grid */
.footer-content {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
}

/* Seções do rodapé */
.footer-section h4 {
    margin-bottom: 1rem;
    color: #ecf0f1;
}

.footer-section p {
    color: #bdc3c7;
    line-height: 1.6;
}

/* Parte inferior do rodapé */
.footer-bottom {
    text-align: center;
    margin-top: 2rem;
    padding-top: 2rem;
    border-top: 1px solid #34495e;
    color: #bdc3c7;
}

/* Media Queries para responsividade mobile */
@media (max-width: 768px) {
    /* Navegação empilhada em mobile */
    .nav-container {
        flex-direction: column;
        gap: 1rem;
    }
    .nav-menu {
        flex-wrap: wrap;
        justify-content: center;
    }  
    /* Hero em coluna no mobile */
    .hero-section {
        flex-direction: column;
        text-align: center;
        gap: 2rem;
    }  
    .hero-content h2 {
        font-size: 2rem;
    }    
    /* Filtros empilhados no mobile */
    .filters {
        flex-direction: column;
        align-items: center;
    }   
    /* Headers empilhados no mobile */
    .dashboard-header,
    .admin-header {
        flex-direction: column;
        text-align: center;
    }   
    /* Grid de estatísticas em coluna única */
    .stats-grid {
        grid-template-columns: 1fr;
    }    
    /* Carrinho em tela cheia no mobile */
    .cart-sidebar {
        width: 100%;
        right: -100%;
    }    
    /* Modal quase tela cheia no mobile */
    .modal-content {
        width: 95%;
        margin: 1rem;
    }    
    /* Tabela menor no mobile */
    .admin-table {
        font-size: 0.9rem;
    }    
    .admin-table th,
    .admin-table td {
        padding: 0.5rem;
    }
}

JS -------------------------------------------------------

// Classe principal do sistema de e-commerce de bebidas
class EcommerceBebidas {
    constructor() {
        this.products = [];           // Array para armazenar todos os produtos
        this.cart = [];              // Array para armazenar itens do carrinho
        this.currentEditingId = null; // ID do produto sendo editado
        this.init();                 // Inicializa o sistema
    }

    // Método de inicialização - configura tudo que é necessário
    init() {
        this.loadInitialData();    // Carrega dados iniciais dos produtos
        this.bindEvents();         // Associa eventos aos elementos
        this.renderProducts();     // Renderiza produtos na tela
        this.updateDashboard();    // Atualiza painel administrativo
        this.renderAdminTable();   // Renderiza tabela de administração
    }

    // Carrega dados iniciais dos produtos (simulando um banco de dados)
    loadInitialData() {
        this.products = [
            {
                id: 1,
                name: "Vinho Tinto Reserva",
                category: "vinho",
                price: 89.90,
                stock: 25,
                description: "Vinho tinto encorpado com notas de frutas vermelhas",
                image: "vinho01.jpg",
                alcohol: 13.5,
                volume: 750
            },
            {
                id: 2,
                name: "Cerveja Artesanal IPA",
                category: "cerveja",
                price: 12.50,
                stock: 48,
                description: "Cerveja India Pale Ale com lúpulo americano",
                image: "ipa.webp",
                alcohol: 5.8,
                volume: 355
            },
            {
                id: 3,
                name: "Whisky Single Malt",
                category: "destilado",
                price: 299.90,
                stock: 8,
                description: "Whisky escocês envelhecido por 12 anos",
                image: "WH-DALMORE-15-SINGLE-MALT-SCOTCH.png",
                alcohol: 40,
                volume: 750
            },
            {
                id: 4,
                name: "Água Mineral Premium",
                category: "nao-alcoolico",
                price: 4.99,
                stock: 120,
                description: "Água mineral natural sem gás",
                image: "agua-sem-gas.png",
                alcohol: 0,
                volume: 500
            },
            {
                id: 5,
                name: "Champagne Brut",
                category: "vinho",
                price: 159.90,
                stock: 15,
                description: "Espumante francês método tradicional",
                image: "1631000-standing-front.png",
                alcohol: 12,
                volume: 750
            },
            {
                id: 6,
                name: "Cachaça Premium",
                category: "destilado",
                price: 45.90,
                stock: 32,
                description: "Cachaça artesanal envelhecida em carvalho",
                image: "cachaca-guaraciaba-extra-premium-carvalho-americano-750ml-01425_1.webp",
                alcohol: 39,
                volume: 700
            }
        ];
    }

    // Associa eventos de clique e interação aos elements HTML
    bindEvents() {
        // Eventos do modal de produto
        document.getElementById('add-product-btn').addEventListener('click', () => this.openProductModal());
        document.getElementById('product-form').addEventListener('submit', (e) => this.handleProductSubmit(e));
        document.getElementById('cancel-btn').addEventListener('click', () => this.closeProductModal());
        document.querySelector('.modal-close').addEventListener('click', () => this.closeProductModal());
        
        // Eventos do modal de confirmação
        document.getElementById('confirm-cancel').addEventListener('click', () => this.closeConfirmModal());
        document.getElementById('confirm-ok').addEventListener('click', () => this.handleConfirmAction());
        
        // Eventos de filtros e busca
        document.getElementById('category-filter').addEventListener('change', () => this.filterProducts());
        document.getElementById('price-filter').addEventListener('change', () => this.filterProducts());
        document.getElementById('search-btn').addEventListener('click', () => this.filterProducts());
        
        // Eventos do carrinho
        document.querySelector('.cart-btn').addEventListener('click', () => this.toggleCart());
        document.querySelector('.cart-close').addEventListener('click', () => this.closeCart());
        document.getElementById('checkout-btn').addEventListener('click', () => this.handleCheckout());
        
        // Eventos do dashboard administrativo
        document.getElementById('refresh-dashboard').addEventListener('click', () => this.updateDashboard());
        document.getElementById('export-report').addEventListener('click', () => this.exportReport());
        
        // Evento para fechar modais clicando fora deles
        document.addEventListener('click', (e) => {
            if (e.target.classList.contains('modal') || e.target.classList.contains('modal-overlay')) {
                this.closeAllModals();
            }
        });

        // Evento para fechar modais com a tecla ESC
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                this.closeAllModals();
            }
        });

        // Evento para scroll suave até a seção de produtos
        document.querySelector('.cta-button').addEventListener('click', () => {
            document.getElementById('produtos').scrollIntoView({ behavior: 'smooth' });
        });
    }

    // Abre o modal para adicionar ou editar produto
    openProductModal(productId = null) {
        const modal = document.getElementById('product-modal');
        const title = document.getElementById('modal-title');
        const form = document.getElementById('product-form');
        
        if (productId) {
            // Modo edição - preenche o formulário com dados existentes
            const product = this.products.find(p => p.id === productId);
            title.textContent = 'Editar Produto';
            this.fillProductForm(product);
            this.currentEditingId = productId;
        } else {
            // Modo adição - formulário vazio
            title.textContent = 'Adicionar Produto';
            form.reset();
            this.clearFormErrors();
            this.currentEditingId = null;
        }
        
        this.showModal(modal);
    }

    // Fecha o modal de produto
    closeProductModal() {
        const modal = document.getElementById('product-modal');
        this.hideModal(modal);
        this.clearFormErrors();
        this.currentEditingId = null;
    }

    // Preenche o formulário com dados do produto para edição
    fillProductForm(product) {
        document.getElementById('product-name').value = product.name;
        document.getElementById('product-category').value = product.category;
        document.getElementById('product-price').value = product.price;
        document.getElementById('product-stock').value = product.stock;
        document.getElementById('product-description').value = product.description || '';
        document.getElementById('product-image').value = product.image || '';
        document.getElementById('product-alcohol').value = product.alcohol || '';
        document.getElementById('product-volume').value = product.volume || '';
    }

    // Processa o envio do formulário de produto
    handleProductSubmit(e) {
        e.preventDefault();
        
        // Valida os dados antes de salvar
        if (!this.validateProductForm()) {
            return;
        }

        // Coleta dados do formulário
        const formData = new FormData(e.target);
        const productData = {
            name: formData.get('name').trim(),
            category: formData.get('category'),
            price: parseFloat(formData.get('price')),
            stock: parseInt(formData.get('stock')),
            description: formData.get('description').trim(),
            image: formData.get('image').trim(),
            alcohol: parseFloat(formData.get('alcohol')) || 0,
            volume: parseInt(formData.get('volume')) || 0
        };

        // Decide se é adição ou edição
        if (this.currentEditingId) {
            this.updateProduct(this.currentEditingId, productData);
        } else {
            this.addProduct(productData);
        }

        this.closeProductModal();
        this.showToast('Produto salvo com sucesso!', 'success');
    }

    // Valida os dados do formulário de produto
    validateProductForm() {
        const name = document.getElementById('product-name').value.trim();
        const category = document.getElementById('product-category').value;
        const price = parseFloat(document.getElementById('product-price').value);
        const stock = parseInt(document.getElementById('product-stock').value);

        let isValid = true;
        this.clearFormErrors();

        // Validação do nome
        if (!name) {
            this.showFieldError('name-error', 'Nome é obrigatório');
            isValid = false;
        }

        // Validação da categoria
        if (!category) {
            this.showFieldError('category-error', 'Categoria é obrigatória');
            isValid = false;
        }

        // Validação do preço
        if (isNaN(price) || price <= 0) {
            this.showFieldError('price-error', 'Preço deve ser maior que zero');
            isValid = false;
        }

        // Validação do estoque
        if (isNaN(stock) || stock < 0) {
            this.showFieldError('stock-error', 'Estoque deve ser maior ou igual a zero');
            isValid = false;
        }

        return isValid;
    }

    // Exibe mensagem de erro em campo específico
    showFieldError(errorId, message) {
        document.getElementById(errorId).textContent = message;
    }

    // Limpa todas as mensagens de erro do formulário
    clearFormErrors() {
        const errorElements = document.querySelectorAll('.error-message');
        errorElements.forEach(el => el.textContent = '');
    }

    // Adiciona novo produto ao sistema
    addProduct(productData) {
        const newId = Math.max(...this.products.map(p => p.id), 0) + 1;
        const newProduct = { id: newId, ...productData };
        this.products.push(newProduct);
        this.renderProducts();
        this.renderAdminTable();
        this.updateDashboard();
    }

    // Atualiza produto existente
    updateProduct(id, productData) {
        const index = this.products.findIndex(p => p.id === id);
        if (index !== -1) {
            this.products[index] = { id, ...productData };
            this.renderProducts();
            this.renderAdminTable();
            this.updateDashboard();
        }
    }

    // Remove produto do sistema após confirmação
    deleteProduct(id) {
        this.confirmAction(`Tem certeza que deseja excluir este produto?`, () => {
            this.products = this.products.filter(p => p.id !== id);
            this.cart = this.cart.filter(item => item.id !== id);
            this.renderProducts();
            this.renderAdminTable();
            this.updateDashboard();
            this.updateCartUI();
            this.showToast('Produto excluído com sucesso!', 'success');
        });
    }

    // Renderiza produtos na grade com filtros aplicados
    renderProducts() {
        const container = document.getElementById('products-grid');
        const categoryFilter = document.getElementById('category-filter').value;
        const priceFilter = document.getElementById('price-filter').value;
        
        let filteredProducts = this.products;

        // Aplica filtro de categoria
        if (categoryFilter) {
            filteredProducts = filteredProducts.filter(p => p.category === categoryFilter);
        }

        // Aplica filtro de preço
        if (priceFilter) {
            const [min, max] = this.parsePriceRange(priceFilter);
            filteredProducts = filteredProducts.filter(p => {
                if (max === Infinity) return p.price >= min;
                return p.price >= min && p.price <= max;
            });
        }

        // Gera HTML dos produtos filtrados
        container.innerHTML = filteredProducts.map(product => `
            <div class="product-card" data-id="${product.id}">
                <div class="product-image">
                    ${product.image ? `<img src="${product.image}" alt="${product.name}">` : '📦 Imagem não disponível'}
                </div>
                <div class="product-info">
                    <div class="product-category">${this.getCategoryName(product.category)}</div>
                    <h3 class="product-name">${product.name}</h3>
                    <div class="product-price">R$ ${product.price.toFixed(2)}</div>
                    <div class="product-stock">Estoque: ${product.stock} unidades</div>
                    <div class="product-actions">
                        <button class="btn primary-btn" onclick="ecommerce.addToCart(${product.id})" ${product.stock === 0 ? 'disabled' : ''}>
                            ${product.stock === 0 ? 'Esgotado' : 'Adicionar'}
                        </button>
                    </div>
                </div>
            </div>
        `).join('');
    }

    // Converte string de filtro de preço em valores mínimo e máximo
    parsePriceRange(range) {
        switch (range) {
            case '0-50': return [0, 50];
            case '50-100': return [50, 100];
            case '100-200': return [100, 200];
            case '200+': return [200, Infinity];
            default: return [0, Infinity];
        }
    }

    // Converte código da categoria em nome amigável
    getCategoryName(category) {
        const names = {
            'vinho': 'Vinho',
            'cerveja': 'Cerveja',
            'destilado': 'Destilado',
            'nao-alcoolico': 'Não Alcoólico'
        };
        return names[category] || category;
    }

    // Aplica filtros e re-renderiza produtos
    filterProducts() {
        this.renderProducts();
    }

    // Adiciona produto ao carrinho de compras
    addToCart(productId) {
        const product = this.products.find(p => p.id === productId);
        if (!product || product.stock === 0) {
            this.showToast('Produto indisponível', 'error');
            return;
        }

        const existingItem = this.cart.find(item => item.id === productId);
        
        if (existingItem) {
            // Produto já está no carrinho - aumenta quantidade
            if (existingItem.quantity < product.stock) {
                existingItem.quantity++;
                this.showToast('Quantidade atualizada no carrinho', 'success');
            } else {
                this.showToast('Estoque insuficiente', 'warning');
                return;
            }
        } else {
            // Novo produto no carrinho
            this.cart.push({
                id: product.id,
                name: product.name,
                price: product.price,
                image: product.image,
                quantity: 1
            });
            this.showToast('Produto adicionado ao carrinho', 'success');
        }

        this.updateCartUI();
    }

    // Remove produto completamente do carrinho
    removeFromCart(productId) {
        this.cart = this.cart.filter(item => item.id !== productId);
        this.updateCartUI();
        this.showToast('Produto removido do carrinho', 'success');
    }

    // Atualiza quantidade de produto no carrinho
    updateCartQuantity(productId, change) {
        const item = this.cart.find(item => item.id === productId);
        const product = this.products.find(p => p.id === productId);
        
        if (item && product) {
            const newQuantity = item.quantity + change;
            
            if (newQuantity <= 0) {
                this.removeFromCart(productId);
                return;
            }
            
            if (newQuantity <= product.stock) {
                item.quantity = newQuantity;
                this.updateCartUI();
            } else {
                this.showToast('Estoque insuficiente', 'warning');
            }
        }
    }

    // Atualiza interface visual do carrinho
    updateCartUI() {
        const cartCount = document.querySelector('.cart-count');
        const cartItems = document.getElementById('cart-items');
        const cartTotal = document.getElementById('cart-total');
        
        // Calcula totais
        const totalItems = this.cart.reduce((sum, item) => sum + item.quantity, 0);
        const totalValue = this.cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        
        // Atualiza elementos da interface
        cartCount.textContent = totalItems;
        cartTotal.textContent = `R$ ${totalValue.toFixed(2)}`;
        
        // Renderiza itens do carrinho
        if (this.cart.length === 0) {
            cartItems.innerHTML = '<div class="empty-cart">Carrinho vazio</div>';
        } else {
            cartItems.innerHTML = this.cart.map(item => `
                <div class="cart-item">
                    <div class="cart-item-image">
                        ${item.image ? `<img src="${item.image}" alt="${item.name}">` : '📦'}
                    </div>
                    <div class="cart-item-info">
                        <div class="cart-item-name">${item.name}</div>
                        <div class="cart-item-price">R$ ${item.price.toFixed(2)}</div>
                        <div class="cart-item-controls">
                            <button class="quantity-btn" onclick="ecommerce.updateCartQuantity(${item.id}, -1)">-</button>
                            <span>${item.quantity}</span>
                            <button class="quantity-btn" onclick="ecommerce.updateCartQuantity(${item.id}, 1)">+</button>
                            <button class="btn danger-btn btn-small" onclick="ecommerce.removeFromCart(${item.id})">Remover</button>
                        </div>
                    </div>
                </div>
            `).join('');
        }
    }

    // Abre/fecha carrinho lateral
    toggleCart() {
        const cartSidebar = document.getElementById('cart-sidebar');
        const overlay = document.getElementById('modal-overlay');
        
        cartSidebar.classList.toggle('active');
        overlay.classList.toggle('active');
    }

    // Fecha carrinho lateral
    closeCart() {
        const cartSidebar = document.getElementById('cart-sidebar');
        const overlay = document.getElementById('modal-overlay');
        
        cartSidebar.classList.remove('active');
        overlay.classList.remove('active');
    }

    // Processa finalização da compra
    handleCheckout() {
        if (this.cart.length === 0) {
            this.showToast('Carrinho vazio', 'warning');
            return;
        }

        const totalValue = this.cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
        
        this.confirmAction(`Finalizar compra no valor de R$ ${totalValue.toFixed(2)}?`, () => {
            // Reduz estoque dos produtos comprados
            this.cart.forEach(item => {
                const product = this.products.find(p => p.id === item.id);
                if (product) {
                    product.stock -= item.quantity;
                }
            });
            
            // Limpa carrinho e atualiza interface
            this.cart = [];
            this.updateCartUI();
            this.renderProducts();
            this.renderAdminTable();
            this.updateDashboard();
            this.closeCart();
            this.showToast('Compra finalizada com sucesso!', 'success');
        });
    }

    // Renderiza tabela administrativa de produtos
    renderAdminTable() {
        const tbody = document.getElementById('admin-table-body');
        
        tbody.innerHTML = this.products.map(product => `
            <tr>
                <td>${product.id}</td>
                <td>
                    <img src="${product.image || ''}" alt="${product.name}" class="product-image-small" 
                         onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
                    <span style="display: none;">📦</span>
                </td>
                <td>${product.name}</td>
                <td>${this.getCategoryName(product.category)}</td>
                <td>R$ ${product.price.toFixed(2)}</td>
                <td>${product.stock}</td>
                <td>
                    <span class="status-badge ${this.getStatusClass(product.stock)}">
                        ${this.getStatusText(product.stock)}
                    </span>
                </td>
                <td>
                    <div class="action-buttons">
                        <button class="btn primary-btn btn-small" onclick="ecommerce.openProductModal(${product.id})">
                            Editar
                        </button>
                        <button class="btn danger-btn btn-small" onclick="ecommerce.deleteProduct(${product.id})">
                            Excluir
                        </button>
                    </div>
                </td>
            </tr>
        `).join('');
    }

    // Retorna classe CSS baseada no status do estoque
    getStatusClass(stock) {
        if (stock === 0) return 'status-out-of-stock';
        if (stock <= 10) return 'status-low-stock';
        return 'status-in-stock';
    }

    // Retorna texto do status baseado no estoque
    getStatusText(stock) {
        if (stock === 0) return 'Esgotado';
        if (stock <= 10) return 'Estoque Baixo';
        return 'Em Estoque';
    }

    // Atualiza painel de controle administrativo
    updateDashboard() {
        // Calcula estatísticas gerais
        const totalProducts = this.products.length;
        const inStock = this.products.filter(p => p.stock > 0).length;
        const outOfStock = this.products.filter(p => p.stock === 0).length;
        const totalValue = this.products.reduce((sum, p) => sum + (p.price * p.stock), 0);
        
        // Atualiza elementos da interface
        document.getElementById('total-products').textContent = totalProducts;
        document.getElementById('in-stock').textContent = inStock;
        document.getElementById('out-of-stock').textContent = outOfStock;
        document.getElementById('total-value').textContent = `R$ ${totalValue.toFixed(2)}`;
        
        this.updateLowStockList();
        this.updateCharts();
    }

    // Atualiza lista de produtos com estoque baixo
    updateLowStockList() {
        const lowStockList = document.getElementById('low-stock-list');
        const lowStockProducts = this.products.filter(p => p.stock <= 10 && p.stock > 0);
        
        if (lowStockProducts.length === 0) {
            lowStockList.innerHTML = '<div class="low-stock-item">Nenhum produto com estoque baixo</div>';
        } else {
            lowStockList.innerHTML = lowStockProducts.map(product => `
                <div class="low-stock-item">
                    <span>${product.name}</span>
                    <span>${product.stock} unidades</span>
                </div>
            `).join('');
        }
    }

    // Atualiza gráficos do dashboard
    updateCharts() {
        this.renderCategoryChart();
        this.renderSalesChart();
    }

    // Renderiza gráfico de pizza por categorias
    renderCategoryChart() {
        const canvas = document.getElementById('category-chart');
        const ctx = canvas.getContext('2d');
        
        // Agrupa produtos por categoria
        const categories = {};
        this.products.forEach(product => {
            const categoryName = this.getCategoryName(product.category);
            categories[categoryName] = (categories[categoryName] || 0) + 1;
        });
        
        this.drawPieChart(ctx, categories, canvas.width, canvas.height);
    }

    // Renderiza gráfico de barras de vendas
    renderSalesChart() {
        const canvas = document.getElementById('sales-chart');
        const ctx = canvas.getContext('2d');
        
        // Dados simulados de vendas por mês
        const salesData = {
            'Jan': 15000,
            'Fev': 18000,
            'Mar': 22000,
            'Abr': 19000,
            'Mai': 25000,
            'Jun': 23000
        };
        
        this.drawBarChart(ctx, salesData, canvas.width, canvas.height);
    }

    // Desenha gráfico de pizza no canvas
    drawPieChart(ctx, data, width, height) {
        ctx.clearRect(0, 0, width, height);
        
        const centerX = width / 2;
        const centerY = height / 2;
        const radius = Math.min(width, height) / 3;
        
        const total = Object.values(data).reduce((sum, value) => sum + value, 0);
        const colors = ['#667eea', '#764ba2', '#f093fb', '#f5576c', '#4facfe', '#00f2fe'];
        
        let currentAngle = 0;
        let colorIndex = 0;
        
        // Desenha cada fatia do gráfico
        Object.entries(data).forEach(([label, value]) => {
            const sliceAngle = (value / total) * 2 * Math.PI;
            
            ctx.beginPath();
            ctx.moveTo(centerX, centerY);
            ctx.arc(centerX, centerY, radius, currentAngle, currentAngle + sliceAngle);
            ctx.closePath();
            ctx.fillStyle = colors[colorIndex % colors.length];
            ctx.fill();
            
            // Adiciona rótulo no centro da fatia
            const labelAngle = currentAngle + sliceAngle / 2;
            const labelX = centerX + Math.cos(labelAngle) * (radius * 0.7);
            const labelY = centerY + Math.sin(labelAngle) * (radius * 0.7);
            
            ctx.fillStyle = '#fff';
            ctx.font = '12px Arial';
            ctx.textAlign = 'center';
            ctx.fillText(value, labelX, labelY);
            
            currentAngle += sliceAngle;
            colorIndex++;
        });
    }

    // Desenha gráfico de barras no canvas
    drawBarChart(ctx, data, width, height) {
        ctx.clearRect(0, 0, width, height);
        
        const margin = 40;
        const chartWidth = width - margin * 2;
        const chartHeight = height - margin * 2;
        
        const maxValue = Math.max(...Object.values(data));
        const barWidth = chartWidth / Object.keys(data).length;
        
        // Desenha fundo do gráfico
        ctx.fillStyle = '#e9ecef';
        ctx.fillRect(margin, margin, chartWidth, chartHeight);
        
        // Desenha cada barra
        Object.entries(data).forEach(([label, value], index) => {
            const barHeight = (value / maxValue) * chartHeight;
            const x = margin + index * barWidth + barWidth * 0.1;
            const y = margin + chartHeight - barHeight;
            
            // Desenha barra
            ctx.fillStyle = '#667eea';
            ctx.fillRect(x, y, barWidth * 0.8, barHeight);
            
            // Adiciona rótulos
            ctx.fillStyle = '#333';
            ctx.font = '12px Arial';
            ctx.textAlign = 'center';
            ctx.fillText(label, x + barWidth * 0.4, height - 10);
            ctx.fillText(`R$ ${(value/1000)}k`, x + barWidth * 0.4, y - 5);
        });
    }

    // Exporta relatório do sistema em formato JSON
    exportReport() {
        const reportData = {
            timestamp: new Date().toISOString(),
            totalProducts: this.products.length,
            inStock: this.products.filter(p => p.stock > 0).length,
            outOfStock: this.products.filter(p => p.stock === 0).length,
            totalValue: this.products.reduce((sum, p) => sum + (p.price * p.stock), 0),
            products: this.products
        };
        
        // Cria arquivo para download
        const dataStr = JSON.stringify(reportData, null, 2);
        const dataBlob = new Blob([dataStr], {type: 'application/json'});
        
        const link = document.createElement('a');
        link.href = URL.createObjectURL(dataBlob);
        link.download = `relatorio-estoque-${new Date().toISOString().split('T')[0]}.json`;
        link.click();
        
        this.showToast('Relatório exportado com sucesso!', 'success');
    }

    // Exibe modal de confirmação para ações críticas
    confirmAction(message, callback) {
        const modal = document.getElementById('confirm-modal');
        const messageEl = document.getElementById('confirm-message');
        
        messageEl.textContent = message;
        this.showModal(modal);
        
        this.pendingConfirmAction = callback;
    }

    // Executa ação confirmada pelo usuário
    handleConfirmAction() {
        if (this.pendingConfirmAction) {
            this.pendingConfirmAction();
            this.pendingConfirmAction = null;
        }
        this.closeConfirmModal();
    }

    // Fecha modal de confirmação
    closeConfirmModal() {
        const modal = document.getElementById('confirm-modal');
        this.hideModal(modal);
        this.pendingConfirmAction = null;
    }

    // Exibe modal com animação
    showModal(modal) {
        modal.classList.add('active');
        modal.setAttribute('aria-hidden', 'false');
        document.body.style.overflow = 'hidden'; // Bloqueia scroll da página
    }

    hideModal(modal) {
        modal.classList.remove('active');
        modal.setAttribute('aria-hidden', 'true');
        document.body.style.overflow = 'auto';
    }

    closeAllModals() {
        const modals = document.querySelectorAll('.modal');
        modals.forEach(modal => this.hideModal(modal));
        this.closeCart();
    }

    showToast(message, type = 'success') {
        const container = document.getElementById('toast-container');
        const toast = document.createElement('div');
        
        toast.className = `toast ${type}`;
        toast.textContent = message;
        
        container.appendChild(toast);
        
        setTimeout(() => {
            toast.remove();
        }, 3000);
    }

    showLoading() {
        const spinner = document.getElementById('loading-spinner');
        spinner.classList.add('active');
        spinner.setAttribute('aria-hidden', 'false');
    }

    hideLoading() {
        const spinner = document.getElementById('loading-spinner');
        spinner.classList.remove('active');
        spinner.setAttribute('aria-hidden', 'true');
    }
}

const ecommerce = new EcommerceBebidas();

document.addEventListener('DOMContentLoaded', () => {
    const navLinks = document.querySelectorAll('.nav-menu a');   
    navLinks.forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const targetId = link.getAttribute('href').substring(1);
            const targetElement = document.getElementById(targetId);    
            if (targetElement) {
                targetElement.scrollIntoView({ behavior: 'smooth' });
            }
        });
    });
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                const id = entry.target.id;
                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href') === `#${id}`) {
                        link.classList.add('active');
                    }
                });
            }
        });
    }, { threshold: 0.5 });
    document.querySelectorAll('section[id]').forEach(section => {
        observer.observe(section);
    });
});
