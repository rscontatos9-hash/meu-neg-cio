<!DOCTYPE html>
<html lang="pt-br">
<head><style>
@font-face {
  font-family: "Optimistic";
  font-style: normal;
  font-weight: 400 600;
  font-display: swap;
  src: url("/fonts/OptimisticAI_VF_Optimized.woff2") format("woff2");
}
@font-face {
  font-family: "Optimistic Mono";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url("/fonts/OptimisticMono_W_TextRegular.woff2") format("woff2");
}
:where(html) {
  font-family: "Optimistic", system-ui, sans-serif;
}
:where(code, pre, kbd, samp) {
  font-family: "Optimistic Mono", ui-monospace, monospace;
}
</style>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
  <title>CONTROL BUSINESS | Gestão de Vendas e Estoque</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
    html, body { width: 100%; overflow-x: hidden; }
    body { background: linear-gradient(160deg, #faf9f4 0%, #f2efe4 50%, #ebe7da 100%); color: #1a1a1a; min-height: 100vh; }
    .app-container { max-width: 1400px; width: 100%; margin: 0 auto; padding: 16px 24px 40px; }
    
    /* HEADER */
    .premium-header {
      background: linear-gradient(135deg, #0f172a 0%, #1e293b 45%, #334155 100%);
      border-radius: 14px; padding: 12px 16px; margin-bottom: 16px; min-height: 52px;
      box-shadow: 0 12px 36px -10px rgba(15,23,42,0.5), inset 0 1px 0 rgba(255,255,255,0.06);
      display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px;
      border: 1px solid rgba(56,189,248,0.2);
    }
    .logo-area { display: flex; align-items: center; gap: 12px; }
    .logo-area h1 { font-size: 1.05rem; font-weight: 700; background: linear-gradient(120deg, #e0f2fe, #38bdf8, #0284c7); -webkit-background-clip: text; background-clip: text; color: transparent; line-height: 1.2; letter-spacing: 0.3px; }
    .logo-area .header-sub { color: #7dd3fc; font-size: 0.66rem; font-weight: 400; letter-spacing: 0.3px; }
    .header-actions { display: flex; gap: 8px; flex-wrap: wrap; align-items: center; }
    .btn-glass {
      background: rgba(255,255,255,0.07); backdrop-filter: blur(6px);
      border: 1px solid rgba(56,189,248,0.3); padding: 7px 14px; border-radius: 30px;
      color: #7dd3fc; font-weight: 600; cursor: pointer; transition: 0.25s;
      display: inline-flex; align-items: center; justify-content: center; gap: 6px; font-size: 0.78rem;
    }
    .btn-glass:hover { background: rgba(255,255,255,0.14); transform: translateY(-1px); border-color: rgba(56,189,248,0.5); }

    /* DASHBOARD */
    .dashboard-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 10px; }
    .toggle-cards-btn { background: none; border: none; font-size: 1.3rem; cursor: pointer; color: #1a1a1a; padding: 4px 10px; border-radius: 30px; transition: 0.2s; }
    .dashboard-cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(210px, 1fr)); gap: 16px; margin-bottom: 24px; }
    .dashboard-cards.hidden { display: none; }
    .card { background: rgba(255,255,255,0.95); backdrop-filter: blur(2px); border-radius: 24px; padding: 18px; box-shadow: 0 10px 28px -8px rgba(15,23,42,0.08), inset 0 1px 0 rgba(255,255,255,0.8); border-top: 4px solid; transition: transform 0.3s cubic-bezier(.25,.46,.45,.94), box-shadow 0.3s; }
    .card:hover { transform: translateY(-4px); }
    .card:nth-child(1) { border-top-color: #0ea5e9; }
    .card:nth-child(2) { border-top-color: #6366f1; }
    .card:nth-child(3) { border-top-color: #0f172a; }
    .card:nth-child(4) { border-top-color: #0284c7; }
    .card i { font-size: 1.8rem; margin-bottom: 10px; }
    .card:nth-child(1) i { color: #0ea5e9; }
    .card:nth-child(2) i { color: #6366f1; }
    .card:nth-child(3) i { color: #0f172a; }
    .card:nth-child(4) i { color: #0284c7; }
    .card h3 { font-size: 0.75rem; font-weight: 700; color: #475569; letter-spacing: 0.6px; text-transform: uppercase; }
    .card .valor { font-size: 1.8rem; font-weight: 800; margin-top: 4px; color: #1a1a1a; word-break: break-word; }

    /* TABS GRID */
    .tabs-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px; margin-bottom: 24px; }
    .tab-grid-btn {
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      gap: 6px; padding: 16px 8px; border-radius: 22px;
      background: rgba(255,255,255,0.96); border: 2px solid transparent;
      box-shadow: 0 2px 12px rgba(15,23,42,0.05), inset 0 1px 0 rgba(255,255,255,0.9);
      cursor: pointer; transition: all 0.3s cubic-bezier(.25,.46,.45,.94);
      text-align: center; min-height: 84px; user-select: none;
    }
    .tab-grid-btn .tab-icon { font-size: 1.45rem; color: #475569; transition: all 0.3s ease; line-height: 1; }
    .tab-grid-btn .tab-label { font-size: 0.78rem; font-weight: 700; color: #1e293b; letter-spacing: 0.2px; line-height: 1.2; }
    .tab-grid-btn.active {
      background: linear-gradient(145deg, #0f172a, #334155);
      color: white; border-color: #020617;
      box-shadow: 0 8px 28px -4px rgba(15,23,42,0.5), inset 0 1px 0 rgba(255,255,255,0.08);
      transform: translateY(-2px);
    }
    .tab-grid-btn.active .tab-icon { color: #38bdf8; }
    .tab-grid-btn.active .tab-label { color: white; }

    /* CARDS & FORMS */
    .tab-pane { display: none; animation: fade 0.25s ease; }
    .tab-pane.active-pane { display: block; }
    @keyframes fade { from { opacity: 0; transform: translateY(4px); } to { opacity: 1; transform: translateY(0); } }
    .glass-card { background: rgba(255,255,255,0.96); border-radius: 28px; padding: 22px; margin-bottom: 22px; box-shadow: 0 6px 28px rgba(15,23,42,0.05), inset 0 1px 0 rgba(255,255,255,0.8); border: 1px solid rgba(56,189,248,0.1); backdrop-filter: blur(2px); }
    .glass-card h3 { color: #0f172a; margin-bottom: 14px; font-size: 1rem; }
    .form-grid { display: flex; flex-wrap: wrap; gap: 12px; align-items: flex-end; }
    .input-group { flex: 1 1 180px; min-width: 140px; }
    .input-group label { font-size: 0.68rem; font-weight: 700; color: #475569; display: block; margin-bottom: 5px; text-transform: uppercase; letter-spacing: 0.5px; }
    input, select { width: 100%; padding: 10px 13px; border-radius: 18px; border: 1.5px solid #cbd5e1; background: #fefefe; font-size: 0.88rem; transition: 0.2s; color: #1a1a1a; }
    input:focus, select:focus { outline: none; border-color: #0ea5e9; box-shadow: 0 0 0 3px rgba(14,165,233,0.2); }
    button { background: linear-gradient(145deg, #0f172a, #334155); border: none; padding: 10px 20px; border-radius: 36px; color: white; font-weight: 600; cursor: pointer; transition: 0.25s; display: inline-flex; align-items: center; justify-content: center; gap: 7px; box-shadow: 0 3px 10px -3px rgba(15,23,42,0.3); font-size: 0.88rem; }
    button:hover { transform: translateY(-1px); filter: brightness(1.1); }
    button.btn-secondary { background: #f1f5f9; color: #1e293b; box-shadow: none; border: 1px solid #cbd5e1; }
    button.btn-danger { background: linear-gradient(145deg, #991b1b, #dc2626); }
    button.btn-warning { background: linear-gradient(145deg, #0369a1, #0ea5e9); color: white; }
    button.btn-sm { padding: 6px 12px; font-size: 0.78rem; }
    button.btn-whatsapp { background: linear-gradient(145deg, #128C7E, #25D366); color: white; }

    /* TABELA CLIENTES */
    .client-table-wrapper { width: 100%; overflow-x: auto; -webkit-overflow-scrolling: touch; border-radius: 20px; border: 1px solid rgba(56,189,248,0.12); background: white; margin-top: 10px; }
    .client-table { width: 100%; border-collapse: collapse; font-size: 0.88rem; min-width: 580px; }
    .client-table th { background: #f8fafc; padding: 12px 12px; text-align: left; font-weight: 700; color: #1e293b; }
    .client-table td { padding: 10px 12px; border-bottom: 1px solid #f1f5f9; vertical-align: middle; }
    .client-detail-row { display: none; background: #f8fafc; }
    .client-detail-row.show { display: table-row; }
    .toggle-details { cursor: pointer; background: none; border: none; font-size: 1.1rem; padding: 4px 8px; color: #475569; box-shadow: none; }
    .acoes-cell { white-space: nowrap; text-align: right; display:flex; gap:5px; flex-wrap:wrap; justify-content:flex-end; }
    .icone-acao { background: #f1f5f9; border: 1px solid #cbd5e1; font-size: 0.75rem; font-weight: 600; padding: 6px 10px; margin: 0 1px; cursor: pointer; border-radius: 30px; transition: 0.15s; color: #334155; box-shadow: none; }
    .icone-acao:hover { background: #e2e8f0; }
    .icone-whats-cob { color: #dc2626; border-color: #fca5a5; }
    .icone-whats-agrad { color: #16a34a; border-color: #86efac; }
    .icone-whats-oferta { color: #ea580c; border-color: #fdba74; }
    .icone-whats-cob:hover { background: #fef2f2; }
    .icone-whats-agrad:hover { background: #f0fdf4; }
    .icone-whats-oferta:hover { background: #fff7ed; }

    /* LISTAS & CARDS INTERNOS */
    .produto-card { background: #f0f9ff; border-left: 4px solid #0ea5e9; border-radius: 18px; padding: 12px 16px; margin-bottom: 7px; }
    .pagamento-card { background: #f0fdf4; border-left: 4px solid #0f172a; border-radius: 18px; padding: 12px 16px; margin-bottom: 7px; }
    .flex-between { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px; }
    .empty-msg { text-align: center; color: #94a3b8; padding: 28px 16px; font-style: italic; }
    
    /* MODAIS */
    .modal-overlay { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(15,23,42,0.55); backdrop-filter: blur(6px); display: flex; align-items: center; justify-content: center; z-index: 2000; visibility: hidden; opacity: 0; transition: 0.25s; padding: 12px; }
    .modal-overlay.active { visibility: visible; opacity: 1; }
    .modal-card { background: white; max-width: 700px; width: 100%; max-height: 85vh; overflow-y: auto; border-radius: 28px; padding: 24px; box-shadow: 0 24px 52px rgba(15,23,42,0.25); }
    .close-modal { float: right; background: none; border: none; font-size: 1.7rem; cursor: pointer; color: #94a3b8; box-shadow: none; padding: 0 6px; }
    .historico-item { background: #f8fafc; border-radius: 18px; padding: 11px; margin-bottom: 8px; border-left: 4px solid #0f172a; }
    
    /* TOAST */
    .toast-notify { position: fixed; bottom: 20px; right: 20px; left: auto; max-width: calc(100vw - 40px); padding: 12px 22px; border-radius: 50px; z-index: 3000; box-shadow: 0 8px 24px rgba(15,23,42,0.3); color: white; font-weight: 500; font-size: 0.88rem; animation: toastIn 0.3s ease; background: linear-gradient(135deg, #0f172a, #334155); border: 1px solid rgba(56,189,248,0.3); text-align: center; }
    @keyframes toastIn { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }

    /* ESTOQUE & CATEGORIAS */
    .category-filters { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 18px; padding: 14px; background: #f8fafc; border-radius: 22px; border: 1px solid rgba(56,189,248,0.1); }
    .cat-btn { display: flex; align-items: center; justify-content: center; width: 100%; padding: 11px 10px; border-radius: 16px; font-weight: 600; font-size: 0.78rem; border: 2px solid transparent; cursor: pointer; color: white; text-align: center; }
    .cat-btn.active { border-color: #020617; box-shadow: 0 0 0 2px rgba(15,23,42,0.3); }
    .estoque-item { background: white; border-radius: 18px; padding: 12px 16px; margin-bottom: 8px; display: flex; justify-content: space-between; align-items: center; border-left: 4px solid; flex-wrap: wrap; gap: 10px; box-shadow: 0 2px 8px rgba(15,23,42,0.03); }
    .categoria-badge { padding: 2px 10px; border-radius: 28px; font-size: 0.68rem; margin-left: 6px; color: white; font-weight: 600; display: inline-block; }
    .qtd-control { display: inline-flex; align-items: center; gap: 6px; background: #f8fafc; padding: 3px 8px; border-radius: 36px; border: 1px solid #cbd5e1; }
    
    /* ALERTA DE ESTOQUE BAIXO */
    .alerta-baixo { background: #fef2f2 !important; border-left-color: #dc2626 !important; border: 1.5px solid #fca5a5 !important; }
    .badge-aviso-baixo { background: #dc2626; color: white; padding: 2px 8px; border-radius: 12px; font-size: 0.65rem; font-weight: 700; margin-left: 8px; animation: pulseBaixo 1.5s infinite; display: inline-flex; align-items: center; gap: 4px; }
    @keyframes pulseBaixo { 0% { opacity: 1; } 50% { opacity: 0.6; } 100% { opacity: 1; } }

    /* RELATÓRIOS & PRECIFICAÇÃO */
    .sales-dashboard { display: flex; flex-wrap: wrap; gap: 18px; margin-bottom: 22px; }
    .total-card { flex: 1 1 250px; background: linear-gradient(135deg, #f0f9ff, #e0f2fe); border-radius: 24px; padding: 18px; text-align: center; border: 1px solid #7dd3fc; }
    .total-card .valor { font-size: 2rem; font-weight: 800; color: #020617; }
    .precificacao-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; }
    .precificacao-col { background: #f8fafc; border-radius: 22px; padding: 18px; border: 1px solid rgba(56,189,248,0.1); display: flex; flex-direction: column; gap: 10px; }
    .precificacao-col h4 { color: #0f172a; font-size: 0.85rem; margin-bottom: 4px; padding-bottom: 8px; border-bottom: 2px solid rgba(56,189,248,0.15); }
    .resultado-precificacao-box { grid-column: 1 / -1; background: linear-gradient(145deg, #f0f9ff, #e0f2fe); border-radius: 22px; padding: 20px; border: 1px solid #7dd3fc; display: grid; grid-template-columns: repeat(auto-fit, minmax(130px, 1fr)); gap: 14px; text-align: center; }
    .res-label { font-size: 0.75rem; font-weight: 700; color: #475569; text-transform: uppercase; margin-bottom: 4px; }
    .res-valor { font-size: 1.25rem; font-weight: 800; color: #0f172a; }

    /* TAGS CATEGORIAS */
    .cat-tags-scroll { display: flex; flex-wrap: nowrap; overflow-x: auto; -webkit-overflow-scrolling: touch; gap: 8px; padding: 14px; margin-top: 14px; background: #f8fafc; border: 1.5px solid rgba(56,189,248,0.15); border-radius: 18px; }
    .cat-tag-pai { flex: 0 0 auto; min-width: 110px; height: 38px; display: inline-flex; align-items: center; justify-content: center; gap: 6px; padding: 0 14px; border-radius: 30px; font-size: 0.78rem; font-weight: 700; color: white; }
    .cat-tag-sub { flex: 0 0 auto; height: 34px; display: inline-flex; align-items: center; gap: 5px; padding: 0 12px; border-radius: 30px; font-size: 0.74rem; font-weight: 600; color: #0c4a6e; background: white; border: 1.5px solid #7dd3fc; }
    .cat-tag-remove { background: none; border: none; color: #94a3b8; cursor: pointer; font-size: 0.68rem; padding: 2px 5px; border-radius: 50%; width: 20px; height: 20px; box-shadow: none; }
    
    /* PESQUISA DE ESTOQUE */
    .stock-search-container { position: relative; margin-bottom: 16px; z-index: 50; }
    .stock-search-header { display: flex; align-items: center; gap: 10px; background: #f8fafc; border: 1.5px solid #cbd5e1; border-radius: 20px; padding: 0 14px; }
    .stock-search-header:focus-within { border-color: #0ea5e9; box-shadow: 0 0 0 3px rgba(14,165,233,0.18); background: white; }
    .stock-search-input { border: none !important; background: transparent !important; box-shadow: none !important; padding: 11px 0 !important; width: 100%; }
    .stock-search-results { position: absolute; top: 100%; left: 0; right: 0; z-index: 100; background: white; border: 1.5px solid #e2e8f0; border-radius: 18px; margin-top: 6px; max-height: 340px; overflow-y: auto; box-shadow: 0 16px 40px rgba(15,23,42,0.14); }
    .stock-search-item { padding: 12px 16px; cursor: pointer; border-bottom: 1px solid #f1f5f9; }
    .stock-search-item:hover { background: #f0f9ff; }
    
    /* CONFIG LOJA */
    .loja-config-card { background: linear-gradient(135deg, #f0fdf4, #dcfce7); border: 1px solid #86efac; border-radius: 16px; padding: 12px 14px; margin-bottom: 14px; display: flex; gap: 10px; align-items: flex-end; flex-wrap: wrap; }
    .chart-wrapper { position: relative; width: 100%; max-height: 360px; }

    /* =================================================================
       MEDIA QUERIES - RESPONSIVIDADE COMPLETA (TABLETS E CELULARES)
       ================================================================= */

    /* Tablets e telas médias (até 900px) */
    @media (max-width: 900px) {
      .app-container { padding: 14px 16px 36px; }
      .tabs-grid { grid-template-columns: repeat(4, 1fr); gap: 10px; }
      .precificacao-grid { grid-template-columns: 1fr; }
    }

    /* Smartphones e telas pequenas (até 640px) */
    @media (max-width: 640px) {
      .app-container { padding: 10px 12px 32px; }
      
      .premium-header { flex-direction: column; align-items: stretch; text-align: center; padding: 14px; }
      .logo-area { justify-content: center; }
      .header-actions { justify-content: center; width: 100%; }
      .btn-glass { flex: 1 1 auto; padding: 8px 10px; font-size: 0.74rem; }

      .loja-config-card { flex-direction: column; align-items: stretch; }
      .loja-config-card .input-group { min-width: 100% !important; }
      .loja-config-card button { width: 100%; }

      .dashboard-cards { grid-template-columns: repeat(2, 1fr); gap: 10px; }
      .card { padding: 14px; border-radius: 18px; }
      .card .valor { font-size: 1.35rem; }
      .card i { font-size: 1.4rem; margin-bottom: 6px; }

      .tabs-grid { grid-template-columns: repeat(2, 1fr); gap: 8px; }
      .tab-grid-btn { min-height: 74px; padding: 12px 6px; border-radius: 18px; }
      .tab-grid-btn .tab-icon { font-size: 1.3rem; }
      .tab-grid-btn .tab-label { font-size: 0.75rem; }

      .glass-card { padding: 16px 14px; border-radius: 22px; margin-bottom: 16px; }
      
      .form-grid { flex-direction: column; align-items: stretch; gap: 10px; }
      .input-group { width: 100%; min-width: 100%; flex: none !important; }
      .form-grid > button { width: 100%; padding: 12px; }

      #tabClientes .flex-between > .input-group { width: 100% !important; }

      .category-filters { grid-template-columns: repeat(2, 1fr); padding: 10px; gap: 8px; }
      
      .estoque-item { flex-direction: column; align-items: flex-start; }
      .estoque-actions { width: 100%; justify-content: space-between; margin-top: 6px; padding-top: 8px; border-top: 1px solid #f1f5f9; }

      .date-card { min-width: 100% !important; flex: none !important; }
      
      .modal-card { padding: 18px 16px; border-radius: 22px; max-height: 88vh; }
      .toast-notify { left: 16px; right: 16px; bottom: 16px; border-radius: 16px; }
    }

    /* Smartphones muito compactos (até 380px) */
    @media (max-width: 380px) {
      .dashboard-cards { grid-template-columns: 1fr; }
      .category-filters { grid-template-columns: 1fr; }
      .resultado-precificacao-box { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
<div class="app-container">
  <div class="premium-header">
    <div class="logo-area"><div><h1><i class="fas fa-briefcase"></i> <span id="headerLojaNome">CONTROL BUSINESS</span></h1><div class="header-sub">Gestão comercial, crédito, fiado e estoque</div></div></div>
    <div class="header-actions">
      <button class="btn-glass" id="exportCSVbtn"><i class="fas fa-file-csv"></i> <span class="btn-label">Relatório CSV</span></button>
      <button class="btn-glass" id="backupJSONbtn"><i class="fas fa-database"></i> <span class="btn-label">Backup</span></button>
      <button class="btn-glass" id="restoreJSONbtn"><i class="fas fa-upload"></i> <span class="btn-label">Restaurar</span></button>
      <input type="file" id="restoreFileInput" accept=".json" style="display:none">
    </div>
  </div>

  <div class="loja-config-card">
    <div class="input-group" style="min-width:220px"><label><i class="fas fa-store"></i> Nome da sua Loja (aparece no WhatsApp)</label><input type="text" id="nomeLojaInput" placeholder="Ex: Loja do Sérgio"></div>
    <button id="btnSalvarLoja" class="btn-whatsapp"><i class="fas fa-save"></i> Salvar Nome</button>
    <span style="font-size:0.75rem;color:#15803d" id="lojaSalvaMsg"></span>
  </div>

  <div class="dashboard-header"><h3><i class="fas fa-chart-simple"></i> Resumo Geral</h3><button id="toggleDashboardCards" class="toggle-cards-btn"><i class="fas fa-chevron-down"></i></button></div>
  <div id="dashboardCardsContainer" class="dashboard-cards hidden">
    <div class="card"><i class="fas fa-users"></i><h3>Total Clientes</h3><div class="valor" id="totalClientes">0</div></div>
    <div class="card"><i class="fas fa-coins"></i><h3>Dívida Total</h3><div class="valor" id="dividaTotal">R$ 0,00</div></div>
    <div class="card"><i class="fas fa-chart-simple"></i><h3>Maior Débito</h3><div class="valor" id="maiorDebito">R$ 0</div></div>
    <div class="card"><i class="fas fa-hand-holding-usd"></i><h3>Recebido (mês)</h3><div class="valor" id="recebidoMes">R$ 0</div></div>
  </div>
  <div class="tabs-grid">
    <button class="tab-grid-btn active" data-tab="tabClientes"><i class="fas fa-user-friends tab-icon"></i><span class="tab-label">Clientes</span></button>
    <button class="tab-grid-btn" data-tab="tabVendas"><i class="fas fa-file-invoice tab-icon"></i><span class="tab-label">Vendas Crédito</span></button>
    <button class="tab-grid-btn" data-tab="tabVendaAvista"><i class="fas fa-shopping-bag tab-icon"></i><span class="tab-label">Venda à Vista</span></button>
    <button class="tab-grid-btn" data-tab="tabPagamentos"><i class="fas fa-money-bill-wave tab-icon"></i><span class="tab-label">Pagamentos</span></button>
    <button class="tab-grid-btn" data-tab="tabVendasRelatorio"><i class="fas fa-chart-line tab-icon"></i><span class="tab-label">Relatório</span></button>
    <button class="tab-grid-btn" data-tab="tabRelatorios"><i class="fas fa-chart-pie tab-icon"></i><span class="tab-label">Analytics</span></button>
    <button class="tab-grid-btn" data-tab="tabEstoque"><i class="fas fa-boxes-stacked tab-icon"></i><span class="tab-label">Estoque</span></button>
    <button class="tab-grid-btn" data-tab="tabCalculadora"><i class="fas fa-calculator tab-icon"></i><span class="tab-label">Precificação</span></button>
  </div>

  <div id="tabClientes" class="tab-pane active-pane">
    <div class="glass-card">
      <h3>Novo Cliente</h3>
      <div class="form-grid">
        <div class="input-group"><label>Nome Completo</label><input type="text" id="novoClienteNome" placeholder="Ex: Maria Silva"></div>
        <div class="input-group"><label><i class="fab fa-whatsapp" style="color:#25D366"></i> WhatsApp (com DDD)</label><input type="text" id="novoClienteWhats" placeholder="(93) 99999-9999"></div>
        <button id="btnAddCliente"><i class="fas fa-save"></i> Adicionar</button>
      </div>
    </div>
    <div class="glass-card">
      <div class="flex-between"><h3>Clientes - Clique no WhatsApp para enviar mensagem</h3><div class="input-group" style="width:240px"><input type="text" id="buscaCliente" placeholder="🔍 Filtrar..."></div></div>
      <div class="client-table-wrapper">
        <table class="client-table"><thead><tr><th style="width:40px"></th><th>Cliente</th><th>WhatsApp</th><th>Ações</th></tr></thead><tbody id="listaClientesRender"></tbody></table>
      </div>
    </div>
  </div>

  <div id="tabVendas" class="tab-pane">
    <div class="glass-card">
      <h3>Registrar Venda a Crédito</h3>
      <div class="form-grid">
        <div class="input-group" style="flex:2"><label>Cliente</label><select id="vendaClienteSelect"><option value="">-- Selecione --</option></select></div>
        <div class="input-group"><label>Produto (do estoque)</label><select id="vendaProdutoSelect"><option value="">-- Selecione --</option></select></div>
        <div class="input-group"><label>Quantidade</label><input id="vendaQtd" type="number" step="any" value="1" min="1"></div>
        <div class="input-group"><label>Preço unitário (R$)</label><input id="vendaPreco" type="number" step="0.01" placeholder="Auto ao selecionar"></div>
        <div class="input-group"><label>Data</label><input id="vendaData" type="date"></div>
        <button id="btnAddVendaEstoque"><i class="fas fa-plus-circle"></i> Lançar Venda</button>
      </div>
      <div class="flex-between" style="margin-top:14px"><h4>Itens do cliente:</h4><strong id="clienteVendaAtualNome"></strong></div>
      <div id="listaProdutosCliente" class="prod-list"></div>
      <div class="flex-between" style="margin-top:16px"><strong style="color:#0f172a">Total pendente: <span id="totalPendenteVenda">R$ 0,00</span></strong><button id="btnZerarCliente" class="btn-secondary"><i class="fas fa-trash-alt"></i> Finalizar conta</button></div>
    </div>
  </div>

  <div id="tabVendaAvista" class="tab-pane">
    <div class="glass-card">
      <h3>Compra à Vista</h3>
      <div class="form-grid">
        <div class="input-group"><label>Produto</label><select id="calcProdutoSelect"><option value="">-- Selecione --</option></select></div>
        <div class="input-group"><label>Quantidade</label><input type="number" id="calcQuantidade" value="1" min="0.01" step="0.01"></div>
        <div class="input-group"><label>Valor Unitário (R$)</label><input id="calcPrecoUnitario" type="number" step="0.01" placeholder="Auto ao selecionar"></div>
        <button id="btnAdicionarItemCompra"><i class="fas fa-plus-circle"></i> Adicionar à lista</button>
      </div>
      <div id="carrinhoCompra" style="margin-top:14px"></div>
      <div class="flex-between" style="margin-top:14px"><strong style="color:#0f172a">Total da Compra: <span id="totalCompra">R$ 0,00</span></strong><button id="btnFinalizarCompra" class="btn-warning"><i class="fas fa-check-double"></i> Finalizar Compra</button></div>
    </div>
  </div>

  <div id="tabPagamentos" class="tab-pane">
    <div class="glass-card">
      <div class="flex-between"><h3>Registrar Pagamento</h3><button id="btnHistoricoGeralPagamentos" class="btn-warning"><i class="fas fa-history"></i> Histórico Geral</button></div>
      <div class="form-grid">
        <div class="input-group"><label>Cliente</label><select id="pagClienteSelect"></select></div>
        <div class="input-group"><label>Valor (R$)</label><input id="pagValor" type="number" step="0.01" placeholder="0,00"></div>
        <div class="input-group"><label>Forma</label><select id="pagForma"><option>Dinheiro</option><option>Pix</option><option>Cartão</option></select></div>
        <div class="input-group"><label>Data</label><input id="pagData" type="date"></div>
        <button id="btnRegistrarPag"><i class="fas fa-check-circle"></i> Registrar</button>
      </div>
      <h4 style="margin-top:16px">Histórico do cliente</h4>
      <div id="historicoPagamentos" class="pay-list"></div>
    </div>
  </div>

  <div id="tabVendasRelatorio" class="tab-pane">
    <div class="glass-card">
      <h3><i class="fas fa-chart-line"></i> Consultar Vendas por Data</h3>
      <div class="sales-dashboard">
        <div class="total-card"><h3><i class="fas fa-calendar-day"></i> Total de Vendas do Dia</h3><div class="valor" id="totalVendasDia">R$ 0,00</div><button id="btnResetVendasDia" class="btn-danger btn-sm" style="margin-top:8px"><i class="fas fa-trash-alt"></i> Resetar Vendas do Dia</button></div>
      </div>
      <div style="display:flex;flex-wrap:wrap;gap:20px;margin-top:18px;">
        <div class="date-card" style="flex:1;background:white;border-radius:22px;padding:18px;border-left:4px solid #0ea5e9;"><h3><i class="fas fa-calendar-alt"></i> Vendas Diretas (à vista)</h3><input type="date" id="dataVendasAvista" style="margin:8px 0"><div class="valor" id="totalAvista" style="font-size:1.6rem;font-weight:800;color:#1a1a1a">R$ 0,00</div><button id="btnBuscarAvista" class="btn-sm btn-secondary">Buscar</button></div>
        <div class="date-card" style="flex:1;background:white;border-radius:22px;padding:18px;border-left:4px solid #0f172a;"><h3><i class="fas fa-calendar-alt"></i> Vendas no Crédito</h3><input type="date" id="dataVendasCredito" style="margin:8px 0"><div class="valor" id="totalCredito" style="font-size:1.6rem;font-weight:800;color:#1a1a1a">R$ 0,00</div><button id="btnBuscarCredito" class="btn-sm btn-secondary">Buscar</button></div>
      </div>
      <div style="margin-top:18px"><div class="flex-between"><h4><i class="fas fa-list"></i> Últimas Vendas Registradas</h4><button id="btnLimparTodasVendas" class="btn-danger btn-sm"><i class="fas fa-trash-alt"></i> Limpar Todas</button></div><div id="listaUltimasVendas" style="max-height:280px;overflow-y:auto;margin-top:10px"></div></div>
    </div>
  </div>

  <div id="tabRelatorios" class="tab-pane">
    <div class="glass-card"><h3>Gráfico de Débitos</h3><div class="chart-wrapper"><canvas id="debtChart"></canvas></div></div>
    <div class="glass-card"><h3>Top clientes</h3><div id="topClientesList"></div></div>
  </div>

  <div id="tabEstoque" class="tab-pane">
    <div class="glass-card">
      <h3><i class="fas fa-tags"></i> Gerenciar Categorias e Subcategorias</h3>
      <div class="form-grid">
        <div class="input-group"><label>Nova Categoria</label><input type="text" id="novaCatNome" placeholder="Ex: Vestuário"></div>
        <button id="btnAddCategoria"><i class="fas fa-plus"></i> Adicionar Cat.</button>
        <div class="input-group"><label>Categoria Pai</label><select id="catPaiSelect"><option value="">-- Selecione --</option></select></div>
        <div class="input-group"><label>Nova Subcategoria</label><input type="text" id="novaSubcatNome" placeholder="Ex: Camisetas"></div>
        <button id="btnAddSubcategoria"><i class="fas fa-plus"></i> Adicionar Sub.</button>
      </div>
      <div id="listaCategoriasGerenciamento" class="cat-tags-scroll"></div>
    </div>
    <div class="glass-card">
      <h3><i class="fas fa-plus-circle"></i> Adicionar/Atualizar Produto</h3>
      <div class="form-grid">
        <div class="input-group"><label>Nome</label><input type="text" id="estoqueProdNome" placeholder="Ex: Produto X"></div>
        <div class="input-group"><label>Quantidade</label><input type="number" id="estoqueQtd" value="0" step="1" min="0"></div>
        <div class="input-group"><label>Unidade</label><select id="estoqueUnidade"><option value="un">Unidade</option><option value="kg">Quilograma (kg)</option><option value="l">Litro (l)</option><option value="m">Metro (m)</option><option value="pacote">Pacote</option><option value="caixa">Caixa</option></select></div>
        <div class="input-group"><label>Preço Custo (R$)</label><input type="number" id="estoquePrecoCusto" step="0.01" placeholder="0,00"></div>
        <div class="input-group"><label>Preço Venda (R$)</label><input type="number" id="estoquePrecoVenda" step="0.01" placeholder="0,00"></div>
        <div class="input-group"><label>Categoria</label><select id="estoqueCategoria"><option value="">-- Selecione --</option></select></div>
        <button id="btnAddEstoque"><i class="fas fa-save"></i> Adicionar</button>
      </div>
      <div style="margin-top:22px">
        <div class="flex-between"><h3><i class="fas fa-boxes"></i> Produtos em Estoque</h3><button id="toggleEstoqueView" class="btn-secondary"><i class="fas fa-eye-slash"></i> Modo Resumo</button></div>
        <div id="categoryFilterContainer" class="category-filters"></div>
        <div id="listaEstoque"></div>
        <div class="flex-between" style="margin-top:18px"><button id="btnExportarEstoque" class="btn-secondary"><i class="fas fa-file-excel"></i> Exportar CSV</button><button id="btnLimparEstoque" class="btn-danger"><i class="fas fa-trash"></i> Limpar Estoque</button></div>
      </div>
    </div>
  </div>

  <div id="tabCalculadora" class="tab-pane">
    <div class="glass-card">
      <h3><i class="fas fa-calculator"></i> Calculadora de Precificação</h3>
      <div class="precificacao-grid">
        <div class="precificacao-col">
          <h4><i class="fas fa-box-open"></i> Custos do Produto</h4>
          <div class="input-group"><label>Preço de Custo (R$)</label><input type="number" id="precoCusto" step="0.01"></div>
          <div class="input-group"><label>Frete por unidade (R$)</label><input type="number" id="precoFrete" step="0.01" value="0"></div>
          <div class="input-group"><label>Impostos (%)</label><input type="number" id="precoImpostos" step="0.1" value="0"></div>
          <div class="input-group"><label>Comissão (%)</label><input type="number" id="precoComissao" step="0.1" value="0"></div>
        </div>
        <div class="precificacao-col">
          <h4><i class="fas fa-receipt"></i> Despesas e Margem</h4>
          <div class="input-group"><label>Desp. Fixas/unidade (R$)</label><input type="number" id="precoDespesasFixas" step="0.01" value="0"></div>
          <div class="input-group"><label>Desp. Variáveis/unidade (R$)</label><input type="number" id="precoDespesasVar" step="0.01" value="0"></div>
          <div class="input-group"><label>Outros custos/unidade (R$)</label><input type="number" id="precoOutros" step="0.01" value="0"></div>
          <div class="input-group"><label>Margem de Lucro (%)</label><input type="number" id="margemLucro" step="0.1" value="50"></div>
        </div>
        <div class="resultado-precificacao-box" id="resultadoPrecificacao">
          <div class="resultado-item"><div class="res-label">Custo Total</div><div class="res-valor" id="resCustoTotal">R$ 0,00</div></div>
          <div class="resultado-item"><div class="res-label">Despesas Total</div><div class="res-valor" id="resDespesasTotal">R$ 0,00</div></div>
          <div class="resultado-item"><div class="res-label">Lucro por Unidade</div><div class="res-valor" id="resLucro">R$ 0,00</div></div>
          <div class="resultado-item"><div class="res-label">Preço de Venda</div><div class="res-valor" id="resPrecoVenda">R$ 0,00</div></div>
        </div>
        <div style="grid-column:1/-1;text-align:center"><button id="btnCalcularPrecoVenda" style="width:100%;max-width:320px"><i class="fas fa-calculator"></i> Calcular Preço</button></div>
      </div>
    </div>
  </div>
</div>

<div id="modalHistoricoGeral" class="modal-overlay"><div class="modal-card"><button class="close-modal" id="fecharModalHistoricoBtn">&times;</button><h3>Histórico Geral de Pagamentos</h3><div id="conteudoHistoricoGeral" style="margin-top:14px"></div></div></div>
<div id="modalInfoCliente" class="modal-overlay"><div class="modal-card"><button class="close-modal" id="fecharModalBtn">&times;</button><h3 id="modalNomeCliente"></h3><div id="modalConteudoInfo" style="margin-top:14px"></div></div></div>

<script>
  // GERADOR DE BIP SONORO (AUDIO CONTEXT)
  function emitirBipEstoque() {
    try {
      const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      const osc = audioCtx.createOscillator();
      const gain = audioCtx.createGain();
      osc.type = 'sine';
      osc.frequency.value = 587.33; // Nota D5 (alerta nítido)
      gain.gain.setValueAtTime(0.15, audioCtx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.00001, audioCtx.currentTime + 0.4);
      osc.connect(gain);
      gain.connect(audioCtx.destination);
      osc.start();
      osc.stop(audioCtx.currentTime + 0.4);
    } catch(e) {
      // Caso o navegador bloqueie autoplay de áudio sem interação prévia
    }
  }

  function salvarArquivoDispositivo(blob, nomeArquivo) {
    try {
      if (navigator.canShare && blob.type.includes('text')) {}
      var url = URL.createObjectURL(blob);
      var a = document.createElement('a');
      a.href = url;
      a.download = nomeArquivo;
      a.style.display = 'none';
      a.setAttribute('target', '_blank');
      document.body.appendChild(a);
      a.click();
      setTimeout(function() { 
        try { document.body.removeChild(a); URL.revokeObjectURL(url); } catch(e){}
      }, 1500);
      showToast("Arquivo baixado: " + nomeArquivo);
    } catch(e) {
      var url = URL.createObjectURL(blob);
      window.open(url, '_blank');
      showToast("Abrindo arquivo: " + nomeArquivo);
    }
  }

  function normalizarTexto(texto) {
    if (!texto) return "";
    return texto.toString().toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g, "");
  }

  // NOME DA LOJA
  let nomeLoja = localStorage.getItem("cb_nome_loja") || "CONTROL BUSINESS";
  document.getElementById("nomeLojaInput").value = nomeLoja !== "CONTROL BUSINESS" ? nomeLoja : "";
  document.getElementById("headerLojaNome").innerText = nomeLoja;
  function salvarNomeLoja(){
    let v = document.getElementById("nomeLojaInput").value.trim();
    if(!v) { v = "CONTROL BUSINESS"; }
    nomeLoja = v;
    localStorage.setItem("cb_nome_loja", v);
    document.getElementById("headerLojaNome").innerText = v;
    document.getElementById("lojaSalvaMsg").innerText = "✓ Salvo: " + v;
    showToast("Nome da loja salvo: " + v);
    setTimeout(()=>{ document.getElementById("lojaSalvaMsg").innerText=""; }, 2500);
  }
  document.getElementById("btnSalvarLoja").addEventListener("click", salvarNomeLoja);

  // CATEGORIAS
  let categoriasCustom = JSON.parse(localStorage.getItem("cb_categorias_custom")) || [];
  const paletteCores = ["#0ea5e9","#6366f1","#8b5cf6","#ec4899","#ef4444","#f59e0b","#10b981","#14b8a6","#0891b2","#3b82f6"];
  let categoryColors = {};
  function salvarCategorias() { localStorage.setItem("cb_categorias_custom", JSON.stringify(categoriasCustom)); atribuirCores(); atualizarSelectCategorias(); renderizarGerenciamentoCategorias(); renderizarEstoque(); atualizarFiltrosCategoria(); }
  function atribuirCores() { categoryColors = {}; categoriasCustom.forEach((cat, idx) => { const cor = paletteCores[idx % paletteCores.length]; categoryColors[cat.nome] = cor; if(cat.subs) { cat.subs.forEach(sub => { categoryColors[cat.nome + " > " + sub] = cor; }); } }); }
  function atualizarSelectCategorias() {
    const selectCat = document.getElementById("estoqueCategoria"); const selectPai = document.getElementById("catPaiSelect");
    let htmlCat = '<option value="">-- Selecione --</option>'; let htmlPai = '<option value="">-- Selecione --</option>';
    categoriasCustom.forEach(cat => {
      if(cat.subs && cat.subs.length > 0) { htmlCat += '<optgroup label="' + escapeHtml(cat.nome) + '">'; cat.subs.forEach(sub => { htmlCat += '<option value="' + escapeHtml(cat.nome) + ' > ' + escapeHtml(sub) + '">' + escapeHtml(sub) + '</option>'; }); htmlCat += '</optgroup>'; }
      else { htmlCat += '<option value="' + escapeHtml(cat.nome) + '">' + escapeHtml(cat.nome) + '</option>'; }
      htmlPai += '<option value="' + escapeHtml(cat.nome) + '">' + escapeHtml(cat.nome) + '</option>';
    });
    selectCat.innerHTML = htmlCat; selectPai.innerHTML = htmlPai;
  }
  function renderizarGerenciamentoCategorias() {
    const container = document.getElementById("listaCategoriasGerenciamento");
    if(!categoriasCustom.length) { container.innerHTML = '<div style="width:100%;text-align:center;color:#94a3b8;font-style:italic;font-size:0.85rem;padding:8px 0">Nenhuma categoria</div>'; return; }
    let html = '';
    categoriasCustom.forEach((cat, idx) => {
      html += '<div class="cat-tag-pai" style="background:' + paletteCores[idx % paletteCores.length] + '"><span>' + escapeHtml(cat.nome) + '</span><button class="cat-tag-remove" style="color:white;background:rgba(0,0,0,0.2)" onclick="removerCategoria(' + idx + ')"><i class="fas fa-times"></i></button></div>';
      if(cat.subs) { cat.subs.forEach((sub, sIdx) => { html += '<div class="cat-tag-sub"><i class="fas fa-angle-right" style="color:#0ea5e9"></i> ' + escapeHtml(sub) + '<button class="cat-tag-remove" onclick="removerSubcategoria(' + idx + ', ' + sIdx + ')"><i class="fas fa-times"></i></button></div>'; }); }
    });
    container.innerHTML = html;
  }
  function adicionarCategoria() { const nome = document.getElementById("novaCatNome").value.trim(); if(!nome) return showToast("Informe o nome da categoria", true); if(categoriasCustom.find(c => c.nome.toLowerCase() === nome.toLowerCase())) return showToast("Categoria já existe", true); categoriasCustom.push({ nome, subs: [] }); salvarCategorias(); document.getElementById("novaCatNome").value = ""; showToast("Categoria adicionada"); }
  function adicionarSubcategoria() { const pai = document.getElementById("catPaiSelect").value; const sub = document.getElementById("novaSubcatNome").value.trim(); if(!pai) return showToast("Selecione a categoria pai", true); if(!sub) return showToast("Informe o nome da subcategoria", true); const cat = categoriasCustom.find(c => c.nome === pai); if(cat.subs.find(s => s.toLowerCase() === sub.toLowerCase())) return showToast("Subcategoria já existe", true); cat.subs.push(sub); salvarCategorias(); document.getElementById("novaSubcatNome").value = ""; showToast("Subcategoria adicionada"); }
  function removerCategoria(idx) { if(confirm('Remover categoria "' + categoriasCustom[idx].nome + '"?')) { categoriasCustom.splice(idx, 1); salvarCategorias(); showToast("Categoria removida"); } }
  function removerSubcategoria(catIdx, subIdx) { categoriasCustom[catIdx].subs.splice(subIdx, 1); salvarCategorias(); showToast("Subcategoria removida"); }

  // HISTORICO VENDAS
  let historicoVendas = JSON.parse(localStorage.getItem("historico_vendas_loja")) || [];
  function salvarHistoricoVendas() { localStorage.setItem("historico_vendas_loja", JSON.stringify(historicoVendas)); }
  function registrarVenda(tipo, clienteNome, produtoNome, quantidade, unidade, valorTotal, data) { historicoVendas.unshift({ id: Date.now() + '-' + Math.random().toString(36).substr(2,4), tipo, cliente: clienteNome, produto: produtoNome, quantidade, unidade, valor: valorTotal, data }); if (historicoVendas.length > 500) historicoVendas = historicoVendas.slice(0, 500); salvarHistoricoVendas(); atualizarUltimasVendas(); atualizarTotalDia(); }
  function atualizarUltimasVendas() { const container = document.getElementById('listaUltimasVendas'); if (!container) return; if (historicoVendas.length === 0) { container.innerHTML = '<div class="empty-msg">Nenhuma venda registrada ainda.</div>'; return; } let html = ''; historicoVendas.slice(0, 50).forEach(v => { html += '<div class="historico-item" style="border-left-color:' + (v.tipo==='crédito'?'#6366f1':'#0ea5e9') + '"><div class="flex-between"><strong>' + escapeHtml(v.cliente) + '</strong><span style="font-weight:700">R$ ' + v.valor.toFixed(2) + '</span></div><div style="font-size:0.8rem;color:#475569">' + escapeHtml(v.produto) + ' | ' + v.quantidade + ' ' + v.unidade + ' | ' + (v.tipo==='crédito'?'📝 Crédito':'💰 À vista') + ' | ' + v.data + '</div></div>'; }); container.innerHTML = html; }
  function buscarVendasPorData(tipo, data) { if (!data) return 0; return historicoVendas.filter(v => v.tipo === tipo && v.data === data).reduce((s, v) => s + v.valor, 0); }
  function atualizarTotalDia() { const hoje = new Date().toISOString().slice(0,10); const total = historicoVendas.filter(v => v.data === hoje).reduce((s, v) => s + v.valor, 0); document.getElementById('totalVendasDia').innerHTML = 'R$ ' + total.toFixed(2); }
  function resetarVendasDoDia() { const hoje = new Date().toISOString().slice(0,10); if (confirm('Remover vendas do dia ' + hoje + '?')) { historicoVendas = historicoVendas.filter(v => v.data !== hoje); salvarHistoricoVendas(); atualizarUltimasVendas(); atualizarTotalDia(); showToast("Vendas do dia resetadas!"); } }
  function limparTodasVendas() { if (!historicoVendas.length) return showToast("Nenhuma venda", true); if (confirm('⚠️ REMOVER TODAS AS ' + historicoVendas.length + ' VENDAS? Ação irreversível!')) { historicoVendas = []; salvarHistoricoVendas(); atualizarUltimasVendas(); atualizarTotalDia(); document.getElementById('totalAvista').innerHTML = 'R$ 0,00'; document.getElementById('totalCredito').innerHTML = 'R$ 0,00'; showToast("Todas as vendas removidas"); } }

  // ESTOQUE
  let estoque = JSON.parse(localStorage.getItem("premium_estoque_loja")) || [];
  let estoqueViewMode = "detailed";
  let activeCategoryFilter = "todas";
  function salvarEstoque() { 
    localStorage.setItem("premium_estoque_loja", JSON.stringify(estoque)); 
    renderizarEstoque(); 
    atualizarFiltrosCategoria(); 
    atualizarSelectsEstoque(); 
  }
  function atualizarFiltrosCategoria() {
    const container = document.getElementById("categoryFilterContainer"); if(!container) return;
    const cats = [...new Set(estoque.map(p => p.categoria).filter(Boolean))];
    let html = '<button class="cat-btn' + (activeCategoryFilter==='todas'?' active':'') + '" data-cat="todas" style="background:#334155">📦 Todas</button>';
    cats.forEach(cat => { html += '<button class="cat-btn' + (activeCategoryFilter===cat?' active':'') + '" data-cat="' + cat + '" style="background:' + (categoryColors[cat]||'#64748b') + '">' + cat + '</button>'; });
    container.innerHTML = html;
    document.querySelectorAll(".cat-btn").forEach(btn => { btn.addEventListener("click", function() { activeCategoryFilter = this.dataset.cat; renderizarEstoque(); atualizarFiltrosCategoria(); }); });
  }
  function renderizarEstoque() {
    const container = document.getElementById("listaEstoque"); if(!container) return;
    let filtered = activeCategoryFilter === "todas" ? estoque : estoque.filter(p => p.categoria === activeCategoryFilter);
    if (!filtered.length) { container.innerHTML = '<div class="empty-msg">Nenhum produto encontrado</div>'; return; }
    
    let temEstoqueBaixo = false;
    container.innerHTML = "";
    filtered.forEach(function(item) {
      const originalIdx = estoque.findIndex(function(p) { return p.nome === item.nome && p.unidade === item.unidade; });
      const precoV = (item.precoVenda || item.precoCusto || 0).toFixed(2);
      
      const estoqueBaixo = item.quantidade <= 5;
      if (estoqueBaixo) temEstoqueBaixo = true;
      
      const div = document.createElement("div"); 
      div.className = "estoque-item" + (estoqueBaixo ? " alerta-baixo" : ""); 
      div.style.borderLeftColor = estoqueBaixo ? "#dc2626" : (categoryColors[item.categoria] || "#64748b");
      
      div.innerHTML = '<div class="estoque-info"><strong>' + escapeHtml(item.nome) + '</strong>' + (estoqueBaixo ? '<span class="badge-aviso-baixo"><i class="fas fa-exclamation-circle"></i> ACABANDO (' + item.quantidade + ')</span>' : '') + (item.categoria ? '<span class="categoria-badge" style="background:' + (categoryColors[item.categoria]||'#334155') + '">' + escapeHtml(item.categoria) + '</span>' : '') + '<div style="font-size:0.8rem;color:#475569;margin-top:3px">' + item.quantidade + ' ' + (item.unidade||'un') + ' | Custo: R$ ' + (item.precoCusto||0).toFixed(2) + ' | <span style="color:#0369a1;font-weight:600">Venda: R$ ' + precoV + '</span></div></div><div class="estoque-actions" style="display:flex;align-items:center;gap:7px"><div class="qtd-control"><button class="btn-sm" data-dec="' + originalIdx + '" style="background:none;box-shadow:none;color:#0f172a;padding:2px 5px"><i class="fas fa-minus"></i></button><span style="font-weight:700;min-width:22px;text-align:center">' + item.quantidade + '</span><button class="btn-sm" data-inc="' + originalIdx + '" style="background:none;box-shadow:none;color:#0f172a;padding:2px 5px"><i class="fas fa-plus"></i></button></div><button class="btn-secondary btn-sm" data-editar="' + originalIdx + '"><i class="fas fa-edit"></i></button><button class="btn-danger btn-sm" data-remover="' + originalIdx + '"><i class="fas fa-trash"></i></button></div>';
      
      div.querySelector("[data-inc]").addEventListener("click", function() { alterarQuantidade(originalIdx, 1); });
      div.querySelector("[data-dec]").addEventListener("click", function() { alterarQuantidade(originalIdx, -1); });
      div.querySelector("[data-editar]").addEventListener("click", function() { editarProdutoEstoque(originalIdx); });
      div.querySelector("[data-remover]").addEventListener("click", function() { removerProdutoEstoque(originalIdx); });
      container.appendChild(div);
    });

    if (temEstoqueBaixo) {
      emitirBipEstoque();
    }
  }
  function alterarQuantidade(idx, delta) { let item = estoque[idx]; if(!item) return; let nova = item.quantidade + delta; if(nova < 0) return showToast("Qtd negativa", true); item.quantidade = nova; salvarEstoque(); showToast(item.nome + ': ' + (delta>0?'+':'') + delta); }
  function adicionarOuAtualizarEstoque() {
    const nome = document.getElementById("estoqueProdNome").value.trim(); const qtd = parseInt(document.getElementById("estoqueQtd").value, 10); const unidade = document.getElementById("estoqueUnidade").value; const precoCusto = parseFloat(document.getElementById("estoquePrecoCusto").value) || 0; const precoVenda = parseFloat(document.getElementById("estoquePrecoVenda").value) || 0; const categoria = document.getElementById("estoqueCategoria").value;
    if(!nome) return showToast("Informe o nome do produto", true); if(isNaN(qtd) || qtd < 0) return showToast("Qtd inválida", true);
    const existing = estoque.findIndex(function(p) { return p.nome.toLowerCase() === nome.toLowerCase() && p.unidade === unidade; });
    if(existing !== -1) { estoque[existing].quantidade += qtd; if(precoCusto) estoque[existing].precoCusto = precoCusto; if(precoVenda) estoque[existing].precoVenda = precoVenda; if(categoria) estoque[existing].categoria = categoria; showToast('Atualizado: +' + qtd + ' ' + unidade); }
    else { estoque.push({ nome, quantidade: qtd, unidade, precoCusto, precoVenda, categoria }); showToast('Adicionado: ' + nome); }
    salvarEstoque(); document.getElementById("estoqueProdNome").value = ""; document.getElementById("estoqueQtd").value = "0"; document.getElementById("estoquePrecoCusto").value = ""; document.getElementById("estoquePrecoVenda").value = ""; document.getElementById("estoqueCategoria").value = "";
  }
  function editarProdutoEstoque(idx) { let item = estoque[idx]; let n = prompt("Nome", item.nome); if(n && n.trim()) item.nome = n.trim(); let q = prompt("Quantidade", item.quantidade); if(q !== null && !isNaN(parseInt(q))) item.quantidade = parseInt(q); let u = prompt("Unidade", item.unidade); if(u) item.unidade = u; let pc = prompt("Preço custo", item.precoCusto||0); if(pc !== null && !isNaN(parseFloat(pc))) item.precoCusto = parseFloat(pc); let pv = prompt("Preço venda", item.precoVenda || item.precoCusto || 0); if(pv !== null && !isNaN(parseFloat(pv))) item.precoVenda = parseFloat(pv); let c = prompt("Categoria", item.categoria); if(c !== null) item.categoria = c; salvarEstoque(); }
  function removerProdutoEstoque(idx) { if(confirm('Remover "' + estoque[idx].nome + '"?')) { estoque.splice(idx,1); salvarEstoque(); showToast("Removido"); } }
  function exportarEstoqueCSV() { if(!estoque.length) return showToast("Estoque vazio", true); let rows = [["Produto","Qtd","Unidade","Preço Custo","Preço Venda","Categoria"]]; estoque.forEach(function(p) { rows.push([p.nome, p.quantidade, p.unidade||'un', (p.precoCusto||0).toFixed(2), (p.precoVenda||p.precoCusto||0).toFixed(2), p.categoria||'']); }); let csv = rows.map(function(r){return r.join(";");}).join("\n"); let blob = new Blob(["\uFEFF"+csv], {type:"text/csv;charset=utf-8"}); salvarArquivoDispositivo(blob, 'estoque_' + Date.now() + '.csv'); showToast("CSV salvo"); }
  function limparEstoque() { if(confirm("Limpar TODO o estoque?")) { estoque = []; salvarEstoque(); showToast("Estoque limpo"); } }
  function atualizarSelectsEstoque() {
    const selectVenda = document.getElementById("vendaProdutoSelect"); const selectCalc = document.getElementById("calcProdutoSelect");
    const options = '<option value="">-- Selecione --</option>' + estoque.map(function(p) { const precoV = p.precoVenda || p.precoCusto || 0; return '<option value="' + escapeHtml(p.nome) + '" data-unid="' + (p.unidade||'un') + '" data-qtd="' + p.quantidade + '" data-preco="' + precoV.toFixed(2) + '">' + escapeHtml(p.nome) + ' (' + p.quantidade + ' ' + (p.unidade||'un') + ' | R$ ' + precoV.toFixed(2) + ')</option>'; }).join('');
    if(selectVenda) selectVenda.innerHTML = options; if(selectCalc) selectCalc.innerHTML = options;
  }

  // CLIENTES - APENAS WHATSAPP
  let clientes = JSON.parse(localStorage.getItem("premium_fiado_loja")) || [];
  clientes.forEach(c=>{ if(c.whatsapp===undefined){ c.whatsapp = c.telefone || ""; } });
  let clienteSelecionadoId = null;
  function saveData() { localStorage.setItem("premium_fiado_loja", JSON.stringify(clientes)); atualizarDashboard(); renderClientesTable(); refreshSelects(); atualizarClienteVendaUI(); atualizarHistoricoPagamentosUI(); renderGraficoDebitos(); }
  function gerarId() { return Date.now() + '-' + Math.random().toString(36).substr(2,6); }
  function showToast(msg, isError) { let t = document.createElement('div'); t.className = 'toast-notify'; if(isError) t.style.background = 'linear-gradient(135deg, #991b1b, #b91c1c)'; t.innerHTML = '<i class="fas ' + (isError?'fa-exclamation-triangle':'fa-check-circle') + '" style="margin-right:8px"></i>' + msg; document.body.appendChild(t); setTimeout(function() { t.style.opacity='0'; t.style.transition='opacity 0.3s'; setTimeout(function(){t.remove();},300); }, 3000); }
  function atualizarDashboard() { let total = clientes.length; let divida = clientes.reduce(function(a,c){return a + (c.totalDebito||0);}, 0); let maior = clientes.length ? Math.max.apply(null, clientes.map(function(c){return c.totalDebito||0;})) : 0; let trinta = new Date(); trinta.setDate(trinta.getDate()-30); let recebido = 0; clientes.forEach(function(c) { (c.pagamentos||[]).forEach(function(p) { if(new Date(p.data) >= trinta) recebido += p.valor; }); }); document.getElementById('totalClientes').innerText = total; document.getElementById('dividaTotal').innerText = 'R$ ' + divida.toFixed(2); document.getElementById('maiorDebito').innerText = 'R$ ' + maior.toFixed(2); document.getElementById('recebidoMes').innerText = 'R$ ' + recebido.toFixed(2); }

  // WHATSAPP FUNÇÕES
  function limparNumeroWhatsApp(num){
    if(!num) return "";
    let n = num.replace(/\D/g, "");
    if(n.length >= 10 && n.length <= 11 && !n.startsWith("55")){ n = "55" + n; }
    return n;
  }
  function abrirWhatsApp(numero, mensagem){
    let numLimpo = limparNumeroWhatsApp(numero);
    if(!numLimpo){ showToast("Cliente sem WhatsApp cadastrado", true); return; }
    let url = "https://wa.me/" + numLimpo + "?text=" + encodeURIComponent(mensagem);
    window.open(url, "_blank");
  }
  function getPrimeiroNome(nomeCompleto){ return nomeCompleto.split(" ")[0]; }

  function enviarWhatsApp(clienteId, tipo){
    let c = clientes.find(x=>x.id===clienteId);
    if(!c){ showToast("Cliente não encontrado", true); return; }
    if(!c.whatsapp){ showToast("Sem WhatsApp para " + c.nome, true); return; }
    let loja = nomeLoja;
    let nome = getPrimeiroNome(c.nome);
    let debito = (c.totalDebito||0).toFixed(2);
    let msg = "";
    if(tipo==="cobranca"){
      if(c.totalDebito<=0){ msg = `Olá ${nome}! 👋 Aqui é da *${loja}*.\n\nPassando para agradecer! Você está em dia conosco. 😊\n\nQualquer coisa estamos à disposição!`; }
      else { msg = `Olá ${nome}! 👋 Aqui é da *${loja}*.\n\nTudo bem? Passando para lembrar que você tem um saldo pendente de *R$ ${debito}* conosco.\n\nSe puder dar uma passadinha para acertar, agradecemos muito! 🙏\n\nQualquer dúvida me chama aqui mesmo.\n*${loja}* - Obrigado pela preferência!`; }
    } else if(tipo==="agradecimento"){
      msg = `Olá ${nome}! 🙏✨\n\nAqui é da *${loja}*.\n\nMuito obrigado pelo seu pagamento! Recebemos com gratidão.\n\nVocê é um cliente muito especial para nós. Volte sempre! 😊\n\n*${loja}*`;
    } else if(tipo==="oferta"){
      let produtoDestaque = estoque.length>0 ? estoque[0].nome : "nossas novidades";
      msg = `Olá ${nome}! 🎉\n\nAqui é da *${loja}* com uma novidade especial para você!\n\nChegou *${produtoDestaque}* e muitas outras ofertas incríveis! 🔥\n\nPasse na loja ou me chama aqui no WhatsApp que te mando fotos e preços.\n\nEstamos te esperando! 😍\n*${loja}*`;
    }
    abrirWhatsApp(c.whatsapp, msg);
  }

  function renderClientesTable(filtro) {
    filtro = filtro || '';
    let filtroNorm = normalizarTexto(filtro);
    let tbody = document.getElementById('listaClientesRender'); 
    let filtrados = clientes.filter(function(c){ return normalizarTexto(c.nome).indexOf(filtroNorm) !== -1; });
    if(!filtrados.length) { tbody.innerHTML = '<tr><td colspan="4" class="empty-msg">Nenhum cliente encontrado</td></tr>'; return; }
    tbody.innerHTML = '';
    filtrados.forEach(function(cli) {
      let row = tbody.insertRow(); 
      let cellToggle = row.insertCell(0); let cellNome = row.insertCell(1); let cellWhats = row.insertCell(2); let cellAcoes = row.insertCell(3);
      let btnToggle = document.createElement('button'); btnToggle.innerHTML = '▼'; btnToggle.className = 'toggle-details';
      let detailRow = tbody.insertRow(); detailRow.className = 'client-detail-row'; let detailCell = detailRow.insertCell(0); detailCell.colSpan = 4;
      btnToggle.onclick = function() { detailRow.classList.toggle('show'); btnToggle.innerHTML = detailRow.classList.contains('show') ? '▲' : '▼'; };
      cellToggle.appendChild(btnToggle);
      cellNome.innerHTML = '<strong style="color:#1a1a1a">' + escapeHtml(cli.nome) + '</strong><br><small style="color:#0369a1">R$ ' + (cli.totalDebito||0).toFixed(2) + '</small>';
      cellWhats.innerHTML = cli.whatsapp ? '<span style="background:#dcfce7;color:#15803d;padding:3px 8px;border-radius:20px;font-size:0.75rem;display:inline-block">' + escapeHtml(cli.whatsapp) + '</span>' : '<small style="color:#94a3b8">sem WhatsApp</small>';
      
      cellAcoes.className = "acoes-cell";
      cellAcoes.innerHTML = 
        '<button class="icone-acao icone-whats-cob" title="Cobrança" data-wcobr="'+cli.id+'">Cobrar</button>' +
        '<button class="icone-acao icone-whats-agrad" title="Agradecer" data-wagr="'+cli.id+'">Agradecer</button>' +
        '<button class="icone-acao icone-whats-oferta" title="Oferta" data-wofer="'+cli.id+'">Oferta</button>' +
        '<button class="icone-acao" title="Info" data-info="'+cli.id+'">Info</button>' +
        '<button class="icone-acao" title="Editar" data-edit="'+cli.id+'">Editar</button>' +
        '<button class="icone-acao" title="Excluir" data-del="'+cli.id+'">Excluir</button>';

      detailCell.innerHTML = '<div style="font-size:0.9rem"><strong>WhatsApp:</strong> ' + (cli.whatsapp||'Não informado') + ' | <strong>Saldo:</strong> <span style="color:#0369a1;font-weight:700">R$ ' + (cli.totalDebito||0).toFixed(2) + '</span></div><div style="margin-top:8px;display:flex;gap:6px;flex-wrap:wrap"><button class="btn-whatsapp btn-sm" data-wcobr="'+cli.id+'">Cobrar</button><button class="btn-whatsapp btn-sm" style="background:linear-gradient(145deg,#15803d,#22c55e)" data-wagr="'+cli.id+'">Agradecer</button><button class="btn-whatsapp btn-sm" style="background:linear-gradient(145deg,#ea580c,#fb923c)" data-wofer="'+cli.id+'">Oferta</button></div>';
      
      row.querySelectorAll("[data-wcobr]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); enviarWhatsApp(b.getAttribute("data-wcobr"), "cobranca"); }));
      row.querySelectorAll("[data-wagr]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); enviarWhatsApp(b.getAttribute("data-wagr"), "agradecimento"); }));
      row.querySelectorAll("[data-wofer]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); enviarWhatsApp(b.getAttribute("data-wofer"), "oferta"); }));
      row.querySelectorAll("[data-info]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); abrirModalInfo(b.getAttribute("data-info")); }));
      row.querySelectorAll("[data-edit]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); editarCliente(b.getAttribute("data-edit")); }));
      row.querySelectorAll("[data-del]").forEach(b=>b.addEventListener("click", e=>{ e.stopPropagation(); excluirCliente(b.getAttribute("data-del")); }));
      
      detailRow.querySelectorAll("[data-wcobr]").forEach(b=>b.addEventListener("click", ()=>enviarWhatsApp(b.getAttribute("data-wcobr"), "cobranca")));
      detailRow.querySelectorAll("[data-wagr]").forEach(b=>b.addEventListener("click", ()=>enviarWhatsApp(b.getAttribute("data-wagr"), "agradecimento")));
      detailRow.querySelectorAll("[data-wofer]").forEach(b=>b.addEventListener("click", ()=>enviarWhatsApp(b.getAttribute("data-wofer"), "oferta")));

      row.onclick = function(e) { if(!e.target.closest('button')) selecionarClienteParaVenda(cli.id); };
    });
  }

  function addCliente(nome, whats) {
    if(!nome.trim()) return showToast("Informe o nome", true);
    let whatsappFinal = whats ? whats.trim() : "";
    if(!whatsappFinal) return showToast("Informe o WhatsApp", true);
    clientes.push({ id: gerarId(), nome: nome.trim(), whatsapp: whatsappFinal, produtos: [], pagamentos: [], totalDebito: 0 });
    saveData(); showToast('Cliente "' + nome.trim() + '" adicionado');
    document.getElementById('novoClienteNome').value = ''; document.getElementById('novoClienteWhats').value = '';
  }
  function editarCliente(id) { let c = clientes.find(function(c){return c.id===id;}); let n = prompt("Nome", c.nome); if(n && n.trim()) c.nome = n.trim(); let w = prompt("WhatsApp (com DDD)", c.whatsapp); if(w!==null) c.whatsapp = w; saveData(); }
  function excluirCliente(id) { if(confirm("Excluir este cliente?")) { clientes = clientes.filter(function(c){return c.id!==id;}); if(clienteSelecionadoId===id) clienteSelecionadoId = null; saveData(); showToast("Cliente removido"); } }
  function selecionarClienteParaVenda(id) { clienteSelecionadoId = id; trocarAba('tabVendas'); let sel = document.getElementById('vendaClienteSelect'); if(sel) sel.value = id; atualizarClienteVendaUI(); }
  
  function atualizarClienteVendaUI() {
    let cli = clientes.find(function(c){return c.id === clienteSelecionadoId;});
    if(!cli) { document.getElementById('listaProdutosCliente').innerHTML = '<div class="empty-msg">Selecione um cliente</div>'; document.getElementById('totalPendenteVenda').innerText = 'R$ 0,00'; document.getElementById('clienteVendaAtualNome').innerHTML = ''; return; }
    document.getElementById('clienteVendaAtualNome').innerHTML = '<i class="fas fa-user-check" style="color:#0ea5e9"></i> ' + escapeHtml(cli.nome) + ' <button class="btn-whatsapp btn-sm" onclick="enviarWhatsApp(\''+cli.id+'\',\'cobranca\')"><i class="fab fa-whatsapp"></i> Cobrar R$ ' + (cli.totalDebito||0).toFixed(2) + '</button>';
    let container = document.getElementById('listaProdutosCliente');
    if(!cli.produtos || !cli.produtos.length) { container.innerHTML = '<div class="empty-msg">Nenhum produto registrado</div>'; } else { 
      container.innerHTML = ''; 
      cli.produtos.forEach(function(p, idx) { 
        let d = document.createElement('div'); 
        d.className = 'produto-card'; 
        d.innerHTML = '<div class="flex-between"><span><strong>' + escapeHtml(p.nome) + '</strong> | ' + p.qtd + ' ' + (p.unidade||'un') + ' x R$ ' + p.preco.toFixed(2) + ' | ' + (p.data||'--') + '</span><span style="display:inline-flex;align-items:center;gap:6px">R$ ' + (p.qtd*p.preco).toFixed(2) + ' <button class="btn-warning btn-sm" title="Estornar produto (devolver ao estoque)" data-estornar="' + idx + '"><i class="fas fa-undo"></i> Estornar</button> <button class="btn-danger btn-sm" data-idx="' + idx + '"><i class="fas fa-times"></i></button></span></div>'; 
        
        d.querySelector('[data-estornar]').addEventListener('click', function() {
          estornarProdutoCliente(cli.id, idx);
        });

        d.querySelector('[data-idx]').addEventListener('click', function() { 
          removerProdutoCliente(cli.id, idx); 
        }); 

        container.appendChild(d); 
      }); 
    }
    document.getElementById('totalPendenteVenda').innerHTML = 'R$ ' + (cli.totalDebito||0).toFixed(2);
  }

  function estornarProdutoCliente(cid, pid) {
    let c = clientes.find(function(c){return c.id===cid;});
    if(!c || !c.produtos[pid]) return;
    let itemEstornado = c.produtos[pid];

    if(confirm(`Deseja estornar "${itemEstornado.nome}" (${itemEstornado.qtd} ${itemEstornado.unidade||'un'})? O produto retornará automaticamente para o estoque.`)) {
      let prodEstoque = estoque.find(function(p){ return normalizarTexto(p.nome) === normalizarTexto(itemEstornado.nome) && (p.unidade||'un') === (itemEstornado.unidade||'un'); });
      if(prodEstoque) {
        prodEstoque.quantidade += itemEstornado.qtd;
      } else {
        estoque.push({
          nome: itemEstornado.nome,
          quantidade: itemEstornado.qtd,
          unidade: itemEstornado.unidade || 'un',
          precoCusto: itemEstornado.preco || 0,
          precoVenda: itemEstornado.preco || 0,
          categoria: 'Estornado'
        });
      }
      salvarEstoque();

      c.produtos.splice(pid, 1);
      recalcularDebitoCliente(c);
      saveData();
      showToast(`Estorno realizado! ${itemEstornado.qtd} ${itemEstornado.unidade||'un'} de "${itemEstornado.nome}" retornou ao estoque.`);
      atualizarClienteVendaUI();
    }
  }

  function removerProdutoCliente(cid, pid) { let c = clientes.find(function(c){return c.id===cid;}); if(c && c.produtos[pid]) { c.produtos.splice(pid,1); recalcularDebitoCliente(c); saveData(); showToast("Item removido"); } }
  function recalcularDebitoCliente(c) { let totalProd = (c.produtos||[]).reduce(function(a,p){return a + (p.qtd*p.preco);}, 0); let totalPago = (c.pagamentos||[]).reduce(function(a,p){return a + p.valor;}, 0); c.totalDebito = Math.max(0, totalProd - totalPago); }

  function addVendaComEstoque() {
    let clienteId = clienteSelecionadoId || document.getElementById('vendaClienteSelect').value; if(!clienteId) return showToast("Selecione um cliente", true);
    const produtoNome = document.getElementById('vendaProdutoSelect').value; if(!produtoNome) return showToast("Selecione um produto", true);
    const qtd = parseFloat(document.getElementById('vendaQtd').value); const preco = parseFloat(document.getElementById('vendaPreco').value);
    const data = document.getElementById('vendaData').value || new Date().toISOString().slice(0,10);
    if(isNaN(qtd) || qtd <= 0) return showToast("Quantidade inválida", true); if(isNaN(preco) || preco <= 0) return showToast("Preço unitário inválido", true);
    
    const produtoEstoque = estoque.find(function(p){return normalizarTexto(p.nome) === normalizarTexto(produtoNome);}); if(!produtoEstoque) return showToast("Produto não encontrado no estoque", true);
    if(produtoEstoque.quantidade < qtd) return showToast('Estoque insuficiente. Disponível: ' + produtoEstoque.quantidade + ' ' + (produtoEstoque.unidade||'un'), true);
    
    produtoEstoque.quantidade -= qtd; 
    salvarEstoque();
    
    let cliente = clientes.find(function(c){return c.id === clienteId;}); if(!cliente) return showToast("Cliente não encontrado", true);
    
    // AGRUPAMENTO AUTOMÁTICO SE O MESMO PRODUTO JÁ ESTIVER NA LISTA DO CLIENTE
    let itemExistente = cliente.produtos.find(function(p){ return normalizarTexto(p.nome) === normalizarTexto(produtoNome) && p.preco === preco; });
    if(itemExistente) {
      itemExistente.qtd += qtd;
      itemExistente.totalItem = itemExistente.qtd * itemExistente.preco;
      itemExistente.data = data;
    } else {
      const valorTotalItem = qtd * preco;
      cliente.produtos.push({ id: gerarId(), nome: produtoNome, qtd, preco, unidade: produtoEstoque.unidade||'un', totalItem: valorTotalItem, data });
    }

    recalcularDebitoCliente(cliente); 
    saveData(); 
    registrarVenda("crédito", cliente.nome, produtoNome, qtd, produtoEstoque.unidade||'un', qtd * preco, data);
    
    document.getElementById('vendaQtd').value = '1'; document.getElementById('vendaPreco').value = ''; document.getElementById('vendaProdutoSelect').value = '';
    showToast('Venda agrupada/lançada: ' + produtoNome + ' (' + qtd + ' ' + (produtoEstoque.unidade||'un') + ')'); 
    atualizarClienteVendaUI();
  }

  function registrarPagamento() { let cid = document.getElementById('pagClienteSelect').value; if(!cid) return showToast("Selecione o cliente", true); let valor = parseFloat(document.getElementById('pagValor').value); if(isNaN(valor) || valor <= 0) return showToast("Valor inválido", true); let forma = document.getElementById('pagForma').value; let data = document.getElementById('pagData').value || new Date().toISOString().slice(0,10); let c = clientes.find(function(c){return c.id===cid;}); c.pagamentos.push({ id: gerarId(), valor, forma, data }); recalcularDebitoCliente(c); saveData(); document.getElementById('pagValor').value = ''; showToast('Pagamento R$ ' + valor.toFixed(2) + ' registrado'); if(confirm("Enviar agradecimento no WhatsApp de " + c.nome + "?")){ enviarWhatsApp(c.id, "agradecimento"); } if(clienteSelecionadoId===cid) atualizarClienteVendaUI(); atualizarHistoricoPagamentosUI(); }
  function atualizarHistoricoPagamentosUI() {
    let cid = document.getElementById('pagClienteSelect').value; if(!cid) { document.getElementById('historicoPagamentos').innerHTML = '<div class="empty-msg">Selecione um cliente</div>'; return; }
    let c = clientes.find(function(c){return c.id===cid;}); if(!c || !c.pagamentos || !c.pagamentos.length) { document.getElementById('historicoPagamentos').innerHTML = '<div class="empty-msg">Sem pagamentos</div>'; return; }
    let cont = document.getElementById('historicoPagamentos'); cont.innerHTML = '';
    c.pagamentos.slice().reverse().forEach(function(p) { let d = document.createElement('div'); d.className = 'pagamento-card'; d.innerHTML = '<div class="flex-between"><span><strong>R$ ' + p.valor.toFixed(2) + '</strong> — ' + p.forma + '</span><span style="font-size:0.8rem;color:#475569">' + p.data + ' <button class="btn-danger btn-sm" data-pag="' + p.id + '"><i class="fas fa-undo-alt"></i></button></span></div>'; d.querySelector('button').addEventListener('click', function() { c.pagamentos = c.pagamentos.filter(function(pg){return pg.id!==p.id;}); recalcularDebitoCliente(c); saveData(); showToast("Pagamento estornado"); if(clienteSelecionadoId===cid) atualizarClienteVendaUI(); atualizarHistoricoPagamentosUI(); }); cont.appendChild(d); });
  }
  function refreshSelects() { let v = document.getElementById('vendaClienteSelect'); let p = document.getElementById('pagClienteSelect'); let opts = '<option value="">-- Selecione --</option>' + clientes.map(function(c){return '<option value="' + c.id + '">' + escapeHtml(c.nome) + ' (R$ ' + (c.totalDebito||0).toFixed(2) + ')</option>';}).join(''); if(v) { v.innerHTML = opts; if(clienteSelecionadoId) v.value = clienteSelecionadoId; } if(p) p.innerHTML = opts; }
  function zerarDividaCliente() { if(!clienteSelecionadoId) return showToast("Selecione cliente", true); if(confirm("Zerar toda a dívida deste cliente?")) { let c = clientes.find(function(c){return c.id===clienteSelecionadoId;}); if(c) { c.produtos = []; c.totalDebito = 0; saveData(); atualizarClienteVendaUI(); showToast('Conta de ' + c.nome + ' zerada'); } } }
  function abrirModalInfo(id) { let c = clientes.find(function(c){return c.id===id;}); if(!c) return; document.getElementById('modalNomeCliente').innerHTML = escapeHtml(c.nome); document.getElementById('modalConteudoInfo').innerHTML = '<p><strong>WhatsApp:</strong> ' + (c.whatsapp||'Não informado') + '</p><p><strong>💰 Saldo:</strong> <span style="color:#0369a1;font-weight:700">R$ ' + (c.totalDebito||0).toFixed(2) + '</span></p><div style="display:flex;gap:6px;margin:10px 0;flex-wrap:wrap"><button class="btn-whatsapp btn-sm" onclick="enviarWhatsApp(\''+c.id+'\',\'cobranca\')"><i class="fab fa-whatsapp"></i> Cobrança</button><button class="btn-whatsapp btn-sm" style="background:linear-gradient(145deg,#15803d,#22c55e)" onclick="enviarWhatsApp(\''+c.id+'\',\'agradecimento\')"><i class="fab fa-whatsapp"></i> Agradecer</button><button class="btn-whatsapp btn-sm" style="background:linear-gradient(145deg,#ea580c,#fb923c)" onclick="enviarWhatsApp(\''+c.id+'\',\'oferta\')"><i class="fab fa-whatsapp"></i> Oferta</button></div><hr style="margin:10px 0"><h4>Últimos produtos:</h4>' + (c.produtos && c.produtos.length ? c.produtos.slice(-5).map(function(p){return '<div class="produto-card">' + p.nome + ' | ' + p.qtd + ' ' + (p.unidade||'un') + ' x R$ ' + p.preco.toFixed(2) + ' = R$ ' + (p.qtd*p.preco).toFixed(2) + '</div>';}).join('') : '<div class="empty-msg">Nenhum</div>') + '<h4 style="margin-top:10px">Últimos pagamentos:</h4>' + (c.pagamentos && c.pagamentos.length ? c.pagamentos.slice(-5).map(function(p){return '<div class="pagamento-card">R$ ' + p.valor.toFixed(2) + ' — ' + p.forma + ' (' + p.data + ')</div>';}).join('') : '<div class="empty-msg">Nenhum</div>'); document.getElementById('modalInfoCliente').classList.add('active'); }
  function exportarNotaCliente(id) { let c = clientes.find(function(c){return c.id===id;}); if(!c) return; let txt = 'CONTROL BUSINESS — NOTA DO CLIENTE\n' + '='.repeat(40) + '\nLoja: ' + nomeLoja + '\nCliente: ' + c.nome + '\nWhatsApp: ' + (c.whatsapp||'-') + '\nDívida: R$ ' + (c.totalDebito||0).toFixed(2) + '\n\nProdutos:\n' + (c.produtos && c.produtos.length ? c.produtos.map(function(p){return p.nome + ' | ' + p.qtd + ' ' + (p.unidade||'un') + ' x R$ ' + p.preco.toFixed(2) + ' = R$ ' + (p.qtd*p.preco).toFixed(2);}).join('\n') : 'Nenhum') + '\n\nPagamentos:\n' + (c.pagamentos && c.pagamentos.length ? c.pagamentos.map(function(p){return 'R$ ' + p.valor.toFixed(2) + ' em ' + p.data + ' (' + p.forma + ')';}).join('\n') : 'Nenhum'); let blob = new Blob([txt], {type:"text/plain;charset=utf-8"}); salvarArquivoDispositivo(blob, 'nota_' + c.nome.replace(/[^a-z0-9]/gi,'_') + '.txt'); showToast("Nota salva"); }
  function renderGraficoDebitos() { let ctx = document.getElementById('debtChart').getContext('2d'); if(window.debtChartInstance) window.debtChartInstance.destroy(); window.debtChartInstance = new Chart(ctx, { type:'bar', data:{ labels: clientes.map(function(c){return c.nome.length>12?c.nome.slice(0,10)+'..':c.nome;}), datasets:[{label:'Débito (R$)', data: clientes.map(function(c){return c.totalDebito||0;}), backgroundColor:'#0ea5e9', borderRadius:8, borderSkipped:false}] }, options:{ responsive:true, maintainAspectRatio:true, plugins:{ legend:{ labels:{ color:'#1e293b' } } }, scales:{ y:{ beginAtZero:true, ticks:{ color:'#475569' } }, x:{ ticks:{ color:'#475569' } } } } }); let topHtml = clientes.slice().sort(function(a,b){return (b.totalDebito||0)-(a.totalDebito||0);}).slice(0,5).map(function(c){return '<div class="flex-between" style="padding:9px 0;border-bottom:1px solid #e2e8f0"><span style="color:#1a1a1a">' + escapeHtml(c.nome) + '</span><strong style="color:#0f172a">R$ ' + (c.totalDebito||0).toFixed(2) + '</strong></div>';}).join(''); document.getElementById('topClientesList').innerHTML = topHtml || '<div class="empty-msg">Sem dados</div>'; }
  function exportarCSV() { let rows = [["Cliente","WhatsApp","Dívida","Itens","Total Pago"]]; clientes.forEach(function(c) { let tp = (c.pagamentos||[]).reduce(function(a,p){return a+p.valor;},0); rows.push([c.nome, c.whatsapp||'-', (c.totalDebito||0).toFixed(2), (c.produtos||[]).length, tp.toFixed(2)]); }); let csv = rows.map(function(r){return r.join(";");}).join("\n"); let blob = new Blob(["\uFEFF"+csv],{type:"text/csv;charset=utf-8"}); salvarArquivoDispositivo(blob, 'relatorio_' + Date.now() + '.csv'); showToast("Relatório CSV salvo"); }
  function backupJSON() { let data = { clientes, estoque, historicoVendas, categoriasCustom, nomeLoja }; let blob = new Blob([JSON.stringify(data,null,2)],{type:"application/json;charset=utf-8"}); salvarArquivoDispositivo(blob, 'backup_control_business_' + Date.now() + '.json'); showToast("Backup salvo"); }
  function restoreJSON(file) { let reader = new FileReader(); reader.onload = function(e) { try { let parsed = JSON.parse(e.target.result); if(parsed.clientes) clientes = parsed.clientes; if(parsed.estoque) estoque = parsed.estoque; if(parsed.historicoVendas) historicoVendas = parsed.historicoVendas; if(parsed.categoriasCustom) categoriasCustom = parsed.categoriasCustom; if(parsed.nomeLoja) { nomeLoja = parsed.nomeLoja; localStorage.setItem("cb_nome_loja", nomeLoja); document.getElementById("nomeLojaInput").value = nomeLoja; document.getElementById("headerLojaNome").innerText = nomeLoja; } salvarCategorias(); saveData(); salvarEstoque(); salvarHistoricoVendas(); showToast("Dados restaurados!"); setTimeout(function() { location.reload(); }, 800); } catch(err) { showToast("Arquivo inválido", true); } }; reader.readAsText(file); }

  function trocarAba(abaId) {
    document.querySelectorAll('.tab-pane').forEach(function(p) { p.classList.remove('active-pane'); });
    document.getElementById(abaId).classList.add('active-pane');
    document.querySelectorAll('.tab-grid-btn').forEach(function(btn) { btn.classList.remove('active'); });
    document.querySelector('.tab-grid-btn[data-tab="' + abaId + '"]').classList.add('active');
    if(abaId==='tabRelatorios') renderGraficoDebitos();
    if(abaId==='tabPagamentos') atualizarHistoricoPagamentosUI();
    if(abaId==='tabVendas') atualizarClienteVendaUI();
    if(abaId==='tabEstoque') { renderizarEstoque(); atualizarFiltrosCategoria(); }
    if(abaId==='tabVendaAvista') { atualizarSelectsEstoque(); atualizarCarrinhoUI(); }
    if(abaId==='tabVendasRelatorio') { atualizarUltimasVendas(); atualizarTotalDia(); }
  }
  function escapeHtml(str) { if(!str) return ''; return str.replace(/[&<>"']/g, function(m) { return ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'})[m]; }); }
  function mostrarHistoricoGeralPagamentos() { let todos = []; clientes.forEach(function(c) { (c.pagamentos||[]).forEach(function(p) { todos.push({ clienteNome: c.nome, valor: p.valor, forma: p.forma, data: p.data }); }); }); if(!todos.length) { document.getElementById('conteudoHistoricoGeral').innerHTML = '<div class="empty-msg">Nenhum pagamento registrado</div>'; } else { todos.sort(function(a,b) { return new Date(b.data)-new Date(a.data); }); document.getElementById('conteudoHistoricoGeral').innerHTML = todos.map(function(p) { return '<div class="historico-item"><div class="flex-between"><strong>' + escapeHtml(p.clienteNome) + '</strong><span style="font-weight:700">R$ ' + p.valor.toFixed(2) + '</span></div><div style="font-size:0.8rem;color:#475569">' + p.forma + ' | ' + p.data + '</div></div>'; }).join(''); } document.getElementById('modalHistoricoGeral').classList.add('active'); }

  let carrinhoItens = [];
  function adicionarItemCompra() { 
    const produtoNome = document.getElementById("calcProdutoSelect").value; 
    if(!produtoNome) return showToast("Selecione um produto", true); 
    const qtd = parseFloat(document.getElementById("calcQuantidade").value); 
    const preco = parseFloat(document.getElementById("calcPrecoUnitario").value); 
    if(isNaN(qtd) || qtd <= 0) return showToast("Quantidade inválida", true); 
    if(isNaN(preco) || preco <= 0) return showToast("Preço inválido", true); 
    
    const produtoEstoque = estoque.find(function(p){return normalizarTexto(p.nome) === normalizarTexto(produtoNome);}); 
    if(!produtoEstoque) return showToast("Produto não encontrado", true); 
    if(produtoEstoque.quantidade < qtd) return showToast("Estoque insuficiente", true); 
    
    // AGRUPAMENTO AUTOMÁTICO NO CARRINHO À VISTA
    let itemExistente = carrinhoItens.find(function(i){ return normalizarTexto(i.nome) === normalizarTexto(produtoNome) && i.precoUnitario === preco; });
    if(itemExistente) {
      itemExistente.quantidade += qtd;
    } else {
      carrinhoItens.push({ nome: produtoNome, quantidade: qtd, precoUnitario: preco, unidade: produtoEstoque.unidade||'un' }); 
    }

    atualizarCarrinhoUI(); 
    document.getElementById("calcQuantidade").value = "1"; 
    document.getElementById("calcPrecoUnitario").value = ""; 
    document.getElementById("calcProdutoSelect").value = ""; 
  }

  function atualizarCarrinhoUI() { const container = document.getElementById("carrinhoCompra"); if(!container) return; if(!carrinhoItens.length) { container.innerHTML = '<div class="empty-msg">Nenhum item adicionado</div>'; document.getElementById("totalCompra").innerText = "R$ 0,00"; return; } let total = 0, html = ''; carrinhoItens.forEach(function(item, idx) { const sub = item.quantidade * item.precoUnitario; total += sub; html += '<div class="produto-card"><div class="flex-between"><span><strong>' + escapeHtml(item.nome) + '</strong> | ' + item.quantidade + ' ' + item.unidade + ' x R$ ' + item.precoUnitario.toFixed(2) + '</span><span>R$ ' + sub.toFixed(2) + ' <button class="btn-danger btn-sm" data-remove="' + idx + '"><i class="fas fa-trash"></i></button></span></div></div>'; }); container.innerHTML = html; document.getElementById("totalCompra").innerText = 'R$ ' + total.toFixed(2); container.querySelectorAll("[data-remove]").forEach(function(btn) { btn.addEventListener("click", function() { carrinhoItens.splice(parseInt(btn.dataset.remove),1); atualizarCarrinhoUI(); }); }); }
  
  function finalizarCompra() { 
    if(!carrinhoItens.length) return showToast("Adicione itens", true); 
    const dataAtual = new Date().toISOString().slice(0,10); 
    let totalGeral = 0; 
    for(let i = 0; i < carrinhoItens.length; i++) { 
      let item = carrinhoItens[i]; 
      let prodIdx = estoque.findIndex(function(p){return normalizarTexto(p.nome) === normalizarTexto(item.nome);}); 
      if(prodIdx === -1) { showToast('Produto "' + item.nome + '" não encontrado', true); return; } 
      if(estoque[prodIdx].quantidade < item.quantidade) { showToast("Estoque insuficiente", true); return; } 
      estoque[prodIdx].quantidade -= item.quantidade; 
      let valorItem = item.quantidade * item.precoUnitario; 
      totalGeral += valorItem; 
      registrarVenda("à vista", "Cliente Avulso", item.nome, item.quantidade, item.unidade, valorItem, dataAtual); 
    } 
    salvarEstoque(); 
    carrinhoItens = []; 
    atualizarCarrinhoUI(); 
    showToast('Compra finalizada! Total: R$ ' + totalGeral.toFixed(2)); 
  }

  function calcularPrecoVenda() {
    const custo = parseFloat(document.getElementById("precoCusto").value) || 0; const frete = parseFloat(document.getElementById("precoFrete").value) || 0;
    const impostosPct = parseFloat(document.getElementById("precoImpostos").value) || 0; const comissaoPct = parseFloat(document.getElementById("precoComissao").value) || 0;
    const despFixas = parseFloat(document.getElementById("precoDespesasFixas").value) || 0; const despVar = parseFloat(document.getElementById("precoDespesasVar").value) || 0;
    const outros = parseFloat(document.getElementById("precoOutros").value) || 0; const margem = parseFloat(document.getElementById("margemLucro").value) || 0;
    if(custo <= 0 && frete <= 0) return showToast("Informe pelo menos o custo ou frete", true);
    const custoBase = custo + frete; const despesasTotais = despFixas + despVar + outros; const custoTotal = custoBase + despesasTotais;
    const deducoesPct = margem + impostosPct + comissaoPct;
    if(deducoesPct >= 100) { showToast("Margem + impostos + comissão ultrapassam 100%", true); return; }
    var precoVenda = custoTotal / (1 - deducoesPct / 100);
    var lucro = precoVenda - custoTotal - (precoVenda * impostosPct / 100) - (precoVenda * comissaoPct / 100);
    document.getElementById('resCustoTotal').innerText = 'R$ ' + custoBase.toFixed(2);
    document.getElementById('resDespesasTotal').innerText = 'R$ ' + despesasTotais.toFixed(2);
    document.getElementById('resLucro').innerText = 'R$ ' + lucro.toFixed(2);
    document.getElementById('resPrecoVenda').innerText = 'R$ ' + precoVenda.toFixed(2);
    showToast('Preço sugerido: R$ ' + precoVenda.toFixed(2));
  }

  document.getElementById('btnAddCliente').addEventListener('click', function() { addCliente(document.getElementById('novoClienteNome').value, document.getElementById('novoClienteWhats').value); });
  document.getElementById('btnAddVendaEstoque').addEventListener('click', addVendaComEstoque);
  document.getElementById('btnRegistrarPag').addEventListener('click', registrarPagamento);
  document.getElementById('btnZerarCliente').addEventListener('click', zerarDividaCliente);
  document.getElementById('exportCSVbtn').addEventListener('click', exportarCSV);
  document.getElementById('backupJSONbtn').addEventListener('click', backupJSON);
  document.getElementById('restoreJSONbtn').addEventListener('click', function() { document.getElementById('restoreFileInput').click(); });
  document.getElementById('restoreFileInput').addEventListener('change', function(e) { if(e.target.files[0]) restoreJSON(e.target.files[0]); e.target.value=''; });
  document.getElementById('buscaCliente').addEventListener('input', function(e) { renderClientesTable(e.target.value); });
  document.getElementById('pagClienteSelect').addEventListener('change', function() { atualizarHistoricoPagamentosUI(); });
  document.getElementById('vendaClienteSelect').addEventListener('change', function(e) { if(e.target.value) { clienteSelecionadoId = e.target.value; atualizarClienteVendaUI(); } });
  document.getElementById('fecharModalBtn').addEventListener('click', function() { document.getElementById('modalInfoCliente').classList.remove('active'); });
  document.getElementById('modalInfoCliente').addEventListener('click', function(e) { if(e.target === document.getElementById('modalInfoCliente')) document.getElementById('modalInfoCliente').classList.remove('active'); });
  document.getElementById('btnHistoricoGeralPagamentos').addEventListener('click', mostrarHistoricoGeralPagamentos);
  document.getElementById('fecharModalHistoricoBtn').addEventListener('click', function() { document.getElementById('modalHistoricoGeral').classList.remove('active'); });
  document.getElementById('modalHistoricoGeral').addEventListener('click', function(e) { if(e.target === document.getElementById('modalHistoricoGeral')) document.getElementById('modalHistoricoGeral').classList.remove('active'); });
  document.querySelectorAll('.tab-grid-btn').forEach(function(btn) { btn.addEventListener('click', function() { trocarAba(btn.getAttribute('data-tab')); }); });
  document.getElementById('btnAddEstoque').addEventListener('click', adicionarOuAtualizarEstoque);
  document.getElementById('btnExportarEstoque').addEventListener('click', exportarEstoqueCSV);
  document.getElementById('btnLimparEstoque').addEventListener('click', limparEstoque);
  document.getElementById('toggleEstoqueView').addEventListener('click', function() { estoqueViewMode = estoqueViewMode === "detailed" ? "summary" : "detailed"; document.getElementById('toggleEstoqueView').innerHTML = estoqueViewMode === "detailed" ? '<i class="fas fa-eye-slash"></i> Modo Resumo' : '<i class="fas fa-list"></i> Modo Detalhado'; renderizarEstoque(); });
  document.getElementById('btnAdicionarItemCompra').addEventListener('click', adicionarItemCompra);
  document.getElementById('btnFinalizarCompra').addEventListener('click', finalizarCompra);
  document.getElementById('btnCalcularPrecoVenda').addEventListener('click', calcularPrecoVenda);
  document.getElementById('toggleDashboardCards').addEventListener('click', function() { var cd = document.getElementById('dashboardCardsContainer'); cd.classList.toggle('hidden'); document.getElementById('toggleDashboardCards').innerHTML = cd.classList.contains('hidden') ? '<i class="fas fa-chevron-down"></i>' : '<i class="fas fa-chevron-up"></i>'; });
  document.getElementById('btnBuscarAvista').addEventListener('click', function(){ const d = document.getElementById('dataVendasAvista').value; if(d) document.getElementById('totalAvista').innerHTML = 'R$ ' + buscarVendasPorData("à vista", d).toFixed(2); });
  document.getElementById('btnBuscarCredito').addEventListener('click', function(){ const d = document.getElementById('dataVendasCredito').value; if(d) document.getElementById('totalCredito').innerHTML = 'R$ ' + buscarVendasPorData("crédito", d).toFixed(2); });
  document.getElementById('btnResetVendasDia').addEventListener('click', resetarVendasDoDia);
  document.getElementById('btnLimparTodasVendas').addEventListener('click', limparTodasVendas);
  document.getElementById('btnAddCategoria').addEventListener('click', adicionarCategoria);
  document.getElementById('btnAddSubcategoria').addEventListener('click', adicionarSubcategoria);

  // PESQUISA ESTOQUE INTELIGENTE (IGNORANDO MAIÚSCULAS/MINÚSCULAS E ACENTOS)
  function criarPesquisaEstoque(tabId, config) {
    var tabEl = document.getElementById(tabId); if (!tabEl) return;
    var glassCard = tabEl.querySelector('.glass-card'); if (!glassCard) return;
    var formGrid = glassCard.querySelector('.form-grid'); if (!formGrid) return;
    var wrapper = document.createElement('div'); wrapper.className = 'stock-search-container';
    wrapper.innerHTML = '<div class="stock-search-header"><i class="fas fa-search ss-icon"></i><input type="text" class="stock-search-input" placeholder="Pesquisar produto (' + estoque.length + ' produtos)..."><span class="stock-search-counter"></span></div><div class="stock-search-results" style="display:none"></div>';
    glassCard.insertBefore(wrapper, formGrid);
    var input = wrapper.querySelector('.stock-search-input'); var results = wrapper.querySelector('.stock-search-results');
    var debounceTimer = null; var estaAberto = false;
    input.addEventListener('input', function() {
      clearTimeout(debounceTimer);
      debounceTimer = setTimeout(function() {
        var termo = normalizarTexto(input.value.trim());
        if (!termo) { results.style.display = 'none'; estaAberto = false; return; }
        var encontrados = estoque.filter(function(p) { 
          return normalizarTexto(p.nome).indexOf(termo) !== -1 || (p.categoria && normalizarTexto(p.categoria).indexOf(termo) !== -1); 
        });
        if (!encontrados.length) { results.innerHTML = '<div class="empty-msg">Nenhum produto</div>'; results.style.display = 'block'; return; }
        var html = '';
        encontrados.forEach(function(p) {
          html += '<div class="stock-search-item" data-pnome="' + escapeHtml(p.nome) + '"><div class="flex-between"><strong>' + escapeHtml(p.nome) + '</strong><span>R$ ' + (p.precoVenda||p.precoCusto||0).toFixed(2) + '</span></div><div style="font-size:0.75rem;color:#64748b">' + p.quantidade + ' ' + (p.unidade||'un') + (p.categoria?' | '+p.categoria:'') + '</div></div>';
        });
        results.innerHTML = html; results.style.display = 'block'; estaAberto = true;
        results.querySelectorAll('.stock-search-item').forEach(function(item) {
          item.addEventListener('click', function() {
            var nomeProduto = this.getAttribute('data-pnome');
            var sel = document.getElementById(config.selectId); if (sel) { sel.value = nomeProduto; sel.dispatchEvent(new Event('change')); }
            input.value = ''; results.style.display = 'none'; estaAberto = false;
          });
        });
      }, 180);
    });
  }
  criarPesquisaEstoque('tabVendaAvista', { selectId: 'calcProdutoSelect' });
  criarPesquisaEstoque('tabVendas', { selectId: 'vendaProdutoSelect' });

  // INICIALIZAÇÃO
  var hoje = new Date().toISOString().slice(0,10);
  document.getElementById('dataVendasAvista').value = hoje;
  document.getElementById('dataVendasCredito').value = hoje;
  document.getElementById('vendaData').value = hoje;
  document.getElementById('pagData').value = hoje;
  clientes.forEach(function(c) { if(c.totalDebito===undefined) recalcularDebitoCliente(c); if(!c.produtos) c.produtos=[]; if(!c.pagamentos) c.pagamentos=[]; });
  atribuirCores(); atualizarSelectCategorias(); renderizarGerenciamentoCategorias();
  saveData(); renderClientesTable(); refreshSelects(); atualizarClienteVendaUI(); atualizarHistoricoPagamentosUI(); renderizarEstoque(); atualizarFiltrosCategoria(); atualizarSelectsEstoque(); atualizarUltimasVendas(); atualizarTotalDia();

  document.getElementById('vendaProdutoSelect').addEventListener('change', function() { const opt = this.options[this.selectedIndex]; const precoInput = document.getElementById('vendaPreco'); if(opt && opt.dataset.preco && parseFloat(opt.dataset.preco) > 0) { precoInput.value = opt.dataset.preco; } });
  document.getElementById('calcProdutoSelect').addEventListener('change', function() { const opt = this.options[this.selectedIndex]; const precoInput = document.getElementById('calcPrecoUnitario'); if(opt && opt.dataset.preco && parseFloat(opt.dataset.preco) > 0) { precoInput.value = opt.dataset.preco; } });
</script>
<script>(function(){var loc=location.href.replace(/#.*$/,"");var ATTR_NAMES=["data-product-id","data-productid","data-product_id","product-id","productid","product_id","data-source-entity-id","source-entity-id","source_entity_id","data-product","data-metadata","data-meta"];var DATASET_KEYS=["productId","productid","product_id","sourceEntityId","sourceentityid","source_entity_id","product","metadata","meta"];function readProductId(value){if(typeof value!=="string"||value.length===0)return null;if(/^[0-9]{6,}$/.test(value))return value;var match=value.match(/(?:product(?:_|-)?id|source(?:_|-)?entity(?:_|-)?id)["'=:\s]+([0-9]{6,})/i);return match?match[1]:null}function extractProductId(start){for(var node=start;node&&node!==document.body;node=node.parentElement){for(var i=0;i<ATTR_NAMES.length;i++){var attrValue=node.getAttribute&&node.getAttribute(ATTR_NAMES[i]);var attrProductId=readProductId(attrValue);if(attrProductId)return attrProductId}var dataset=node.dataset||null;if(dataset){for(var j=0;j<DATASET_KEYS.length;j++){var dataValue=dataset[DATASET_KEYS[j]];var dataProductId=readProductId(dataValue);if(dataProductId)return dataProductId}}}return null}function isInlineMediaSlotElement(node){return !!(node&&node.getAttribute&&node.getAttribute("data-clippy-inline-media-slot")!==null)}function findInlineMediaSlot(start){for(var node=start;node&&node!==document.body;node=node.parentElement){if(isInlineMediaSlotElement(node))return node}return null}function readInlineMediaUrl(node){if(!node)return null;return node.getAttribute&&((node.getAttribute("data-clippy-inline-media-url")||node.getAttribute("data-url")||node.getAttribute("data_url")))||node.href||null}function stripHash(url){return String(url).replace(/#.*$/,"")}function urlsMatch(a,b){if(!a||!b)return false;try{return stripHash(new URL(a,loc).href)===stripHash(new URL(b,loc).href)}catch(_){return stripHash(a)===stripHash(b)}}function isFirstPartyReelUrl(value){try{var url=new URL(value,loc);if(url.protocol!=="https:")return false;var host=url.hostname.toLowerCase();var supported=host==="instagram.com"||host.endsWith(".instagram.com")||host==="facebook.com"||host.endsWith(".facebook.com");return supported&&/\/reels?\//i.test(url.pathname)}catch(_){return false}}function isInlineMediaUrlClick(node,href){var slot=findInlineMediaSlot(node);if(!slot)return false;var slotUrl=readInlineMediaUrl(slot);if(slotUrl)return urlsMatch(href,slotUrl);return isFirstPartyReelUrl(href)}function findDataHref(start){for(var node=start;node&&node!==document.body;node=node.parentElement){if(node.getAttribute){var href=node.getAttribute("data-href")||node.getAttribute("data-url");if(href)return{href:href,node:node}}}return null}var nativeOpen=window.open;window.open=function(url){if(parent!==window&&typeof url==="string"&&/^https?:\/\//.test(url)){parent.postMessage({type:"ecto:usercontent-link-click",href:url},"*");return null}return nativeOpen?nativeOpen.apply(window,arguments):null};document.addEventListener("click",function(e){var target=e.target instanceof Element?e.target:null;if(!target)return;if(parent===window)return;var a=target.closest?target.closest("a[href]"):null;if(a&&a.href&&/^https?:\/\//.test(a.href)&&a.href.replace(/#.*$/,"")!==loc){if(isInlineMediaUrlClick(a,a.href))return;var productId=extractProductId(target)||extractProductId(a);if(productId){e.preventDefault();parent.postMessage({type:"ecto-artifact-link-click",productId:productId},"*");return}e.preventDefault();parent.postMessage({type:"ecto:usercontent-link-click",href:a.href},"*");return}var dataHref=findDataHref(target);if(dataHref&&/^https?:\/\//.test(dataHref.href)&&dataHref.href.replace(/#.*$/,"")!==loc){if(isInlineMediaUrlClick(dataHref.node,dataHref.href))return;e.preventDefault();parent.postMessage({type:"ecto:usercontent-link-click",href:dataHref.href},"*")}},true)})();</script><script>(function(){var FOCUS_TYPE="ecto:artifact-focus-request";var CLOSE_TYPE="ecto:artifact-close-request";function focusArtifactDocument(){var body=document.body;if(!body)return;try{window.focus();}catch(e){}if(!body.hasAttribute("tabindex"))body.setAttribute("tabindex","-1");try{body.focus({preventScroll:true});}catch(e){try{body.focus();}catch(e2){}}}window.name="";window.addEventListener("message",function(event){if(event.source!==window.parent)return;var data=event.data;if(!data||typeof data!=="object"||data.type!==FOCUS_TYPE)return;if(document.readyState==="loading"){document.addEventListener("DOMContentLoaded",focusArtifactDocument,{once:true});return;}focusArtifactDocument();});window.addEventListener("keydown",function(event){if(event.key!=="Escape")return;window.setTimeout(function(){if(event.defaultPrevented)return;window.parent.postMessage({type:CLOSE_TYPE},"*");},0);});})();</script></body>
</html>
