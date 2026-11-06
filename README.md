<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Pesquisa Justa - Sistema de Opinião Pública</title>
    <style>
        :root {
            --bg-color: #090d16;
            --card-bg: #131c31;
            --primary: #334155;
            --primary-hover: #475569;
            --accent: #0f766e;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border: #334155;
            --focus-ring: #38bdf8;
            --highlight-yellow: #facc15;
        }

        html, body {
            min-height: 100vh;
            width: 100vw;
            margin: 0;
            padding: 0;
            background-color: var(--bg-color);
            color: var(--text-main);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            box-sizing: border-box;
        }

        .phone-frame {
            width: 100%;
            max-width: 420px;
            min-height: 100vh;
            background-color: var(--card-bg);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            box-sizing: border-box;
            box-shadow: 0 10px 25px rgba(0,0,0,0.6);
            border-left: 2px solid var(--border);
            border-right: 2px solid var(--border);
        }

        .screen {
            flex: 1;
            display: flex;
            flex-direction: column;
            padding: 10px 12px;
            box-sizing: border-box;
        }

        .app-brand-header {
            text-align: center;
            background: linear-gradient(135deg, rgba(15, 118, 110, 0.25) 0%, rgba(56, 189, 248, 0.15) 100%);
            border: 1px solid #38bdf8;
            border-radius: 6px;
            padding: 5px;
            margin-bottom: 5px;
        }
        .app-brand-header h1 {
            font-size: 0.92rem;
            font-weight: 900;
            color: #38bdf8;
            letter-spacing: 0.5px;
            text-transform: uppercase;
            margin: 0;
        }
        .app-brand-header p {
            margin: 0;
            font-size: 0.52rem;
            color: var(--text-muted);
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        .status-banner {
            background-color: rgba(56, 189, 248, 0.1);
            border: 1px solid #38bdf8;
            border-radius: 6px;
            padding: 4px 6px;
            text-align: center;
            font-size: 0.60rem;
            color: var(--highlight-yellow);
            font-weight: bold;
            margin-bottom: 5px;
        }

        .tse-notice-box {
            background-color: rgba(15, 118, 110, 0.15);
            border: 1px solid #0f766e;
            border-radius: 6px;
            padding: 4px 6px;
            text-align: center;
            margin-bottom: 6px;
        }
        .tse-notice-box span {
            font-size: 0.50rem;
            color: #38bdf8;
            font-weight: bold;
            display: block;
        }
        .tse-notice-box p {
            margin: 0;
            font-size: 0.46rem;
            color: var(--text-muted);
            line-height: 1.1;
        }

        .screen-content {
            flex: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        h1, h2, h3 {
            margin: 0;
        }

        .header-title {
            font-size: 0.82rem;
            font-weight: bold;
            color: var(--text-main);
            text-align: center;
        }

        .subtitle {
            font-size: 0.55rem;
            color: var(--text-muted);
            text-align: center;
        }

        .form-row {
            display: flex;
            gap: 6px;
            margin-bottom: 6px;
        }

        .form-group {
            flex: 1;
            min-width: 0;
        }

        label {
            display: block;
            font-size: 0.52rem;
            color: var(--text-muted);
            margin-bottom: 2px;
            font-weight: 600;
            text-align: left;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        input, select {
            width: 100%;
            padding: 6px 4px;
            background-color: #090d16;
            border: 1px solid var(--border);
            border-radius: 6px;
            color: var(--text-main);
            font-size: 0.65rem;
            box-sizing: border-box;
            text-align: center;
            text-align-last: center;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--focus-ring);
            box-shadow: 0 0 0 2px rgba(56, 189, 248, 0.25);
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 0.50rem;
            color: var(--text-main);
            line-height: 1.2;
            margin: 6px 0;
        }

        .checkbox-group input {
            width: 14px;
            height: 14px;
            margin: 0;
            accent-color: var(--accent);
            cursor: pointer;
        }

        button {
            width: 100%;
            padding: 9px;
            background-color: #1e293b;
            color: white;
            border: 1px solid #475569;
            border-radius: 6px;
            font-size: 0.68rem;
            font-weight: bold;
            cursor: pointer;
            margin-top: 4px;
        }

        #candidates-container {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .candidate-card {
            background-color: #090d16;
            border: 2px solid var(--border);
            border-radius: 6px;
            padding: 6px 8px;
            display: flex;
            align-items: center;
            cursor: pointer;
        }

        .candidate-card.selected {
            border-color: #10b981;
            background-color: rgba(16, 185, 129, 0.08);
            box-shadow: 0 0 0 2px rgba(16, 185, 129, 0.3);
        }

        .candidate-img {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            object-fit: cover;
            margin-right: 8px;
            border: 1px solid var(--border);
        }

        .candidate-info h4 {
            margin: 0 0 1px 0;
            font-size: 0.72rem;
        }

        .candidate-info p {
            margin: 0;
            font-size: 0.52rem;
            color: var(--text-muted);
        }

        .special-votes-wrapper {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 6px;
            margin: 6px 0;
        }

        .special-vote-btn {
            background-color: #1e293b;
            border: 1px dashed var(--border);
            text-align: center;
            padding: 6px 4px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.55rem;
            color: var(--text-muted);
        }
        .special-vote-btn.selected {
            border-color: #10b981;
            background-color: rgba(16, 185, 129, 0.15);
            color: #10b981;
        }

        .pattern-lock-container {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 12px;
            width: 160px;
            margin: 10px auto;
            padding: 10px;
            background-color: #090d16;
            border: 1px solid var(--border);
            border-radius: 8px;
            justify-items: center;
            align-items: center;
        }
        .pattern-dot {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            background-color: #334155;
            border: 2px solid var(--border);
            cursor: pointer;
            transition: all 0.2s;
        }
        .pattern-dot.active {
            background-color: var(--accent);
            border-color: #38bdf8;
            box-shadow: 0 0 8px #38bdf8;
        }

        .hidden {
            display: none !important;
        }

        .success-box {
            text-align: center;
            padding: 16px 8px;
        }

        .success-icon {
            font-size: 2.2rem;
            color: #10b981;
            margin-bottom: 6px;
        }

        .badge {
            display: inline-block;
            background-color: rgba(100, 116, 139, 0.2);
            color: #94a3b8;
            padding: 3px 8px;
            border-radius: 10px;
            font-size: 0.52rem;
            font-weight: bold;
            text-transform: uppercase;
        }

        .result-tabs {
            display: flex;
            flex-direction: row;
            gap: 4px;
            background-color: #090d16;
            padding: 3px;
            border-radius: 6px;
            border: 1px solid var(--border);
            margin-bottom: 6px;
        }
        .tab-btn {
            flex: 1;
            min-width: 0;
            padding: 5px 3px;
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-size: 0.52rem;
            font-weight: bold;
            border-radius: 4px;
            cursor: pointer;
            text-align: center;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .tab-btn.active {
            background-color: var(--primary);
            color: white;
        }

        .filter-box {
            background-color: #090d16;
            padding: 6px 8px;
            border-radius: 6px;
            border: 1px solid var(--border);
            font-size: 0.54rem;
            margin-bottom: 6px;
        }

        .sub-filters {
            display: flex;
            flex-wrap: wrap;
            gap: 4px;
            margin-top: 4px;
        }
        .sub-filter-btn {
            padding: 3px 6px;
            background: #1e293b;
            border: 1px solid var(--border);
            color: var(--text-muted);
            font-size: 0.50rem;
            border-radius: 4px;
            cursor: pointer;
        }
        .sub-filter-btn.active {
            background-color: var(--accent);
            color: white;
            border-color: #14b8a6;
        }

        .section-divider {
            margin: 4px 0;
            border-top: 1px dashed var(--border);
            padding-top: 4px;
            font-size: 0.48rem;
            font-weight: bold;
            color: #38bdf8;
            text-transform: uppercase;
            text-align: center;
        }

        .mode-toggle {
            display: flex;
            background-color: #090d16;
            border: 1px solid var(--border);
            border-radius: 6px;
            padding: 3px;
            margin-bottom: 6px;
        }
        .mode-btn {
            flex: 1;
            padding: 5px;
            background: transparent;
            border: none;
            color: var(--text-muted);
            font-size: 0.52rem;
            font-weight: bold;
            cursor: pointer;
            border-radius: 4px;
            margin-top: 0;
        }
        .mode-btn.active {
            background-color: var(--accent);
            color: white;
        }

        .result-bar-container {
            margin-bottom: 6px;
        }

        .result-meta {
            display: flex;
            justify-content: space-between;
            font-size: 0.58rem;
            margin-bottom: 2px;
        }

        .progress-bar {
            width: 100%;
            height: 6px;
            background-color: #090d16;
            border-radius: 3px;
            overflow: hidden;
            border: 1px solid var(--border);
        }

        .progress-fill {
            height: 100%;
            background-color: #0f766e;
            border-radius: 3px;
            width: 0%;
        }

        .admin-stat-card {
            background-color: #090d16;
            border: 1px solid var(--border);
            border-radius: 6px;
            padding: 6px;
            text-align: center;
        }
        .admin-stat-card h3 {
            margin: 0;
            font-size: 0.85rem;
            color: #38bdf8;
        }
        .admin-stat-card p {
            margin: 0;
            font-size: 0.48rem;
            color: var(--text-muted);
        }

        .report-preview-box {
            background-color: #ffffff;
            color: #0f172a;
            border-radius: 6px;
            padding: 12px;
            font-size: 0.60rem;
            text-align: left;
            box-sizing: border-box;
            margin: 6px 0;
            box-shadow: 0 2px 8px rgba(0,0,0,0.3);
            flex: 1;
            overflow-y: auto;
        }
        .report-preview-box h3 {
            color: #0f766e;
            text-align: center;
            margin-bottom: 4px;
            font-size: 0.72rem;
        }
        .report-section-title {
            background-color: #f1f5f9;
            color: #0f766e;
            padding: 4px 6px;
            font-weight: bold;
            font-size: 0.58rem;
            border-left: 3px solid #0f766e;
            margin: 6px 0 4px 0;
            text-transform: uppercase;
        }
        .report-preview-box hr {
            border: 0;
            border-top: 1px solid #cbd5e1;
            margin: 6px 0;
        }

        .external-sponsor-banner {
            width: 100%;
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            border-top: 1px dashed #475569;
            padding: 6px 8px;
            text-align: center;
            box-sizing: border-box;
            margin-top: auto;
        }
        .external-sponsor-banner span {
            font-size: 0.40rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: var(--text-muted);
            display: block;
        }
        .external-sponsor-banner p {
            margin: 0;
            font-size: 0.54rem;
            color: #38bdf8;
            font-weight: bold;
        }

        #toast-container {
            position: absolute;
            bottom: 25px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #10b981;
            color: white;
            padding: 10px 16px;
            border-radius: 8px;
            font-size: 0.60rem;
            font-weight: bold;
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
            z-index: 9999;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s, visibility 0.3s;
            text-align: center;
            white-space: nowrap;
        }
        #toast-container.show {
            opacity: 1;
            visibility: visible;
        }
        #toast-container.error {
            background-color: #ef4444;
        }

        @media print {
            body * {
                visibility: hidden;
            }
            #report-content-box, #report-content-box * {
                visibility: visible;
                font-size: 12pt !important;
                color: #000 !important;
            }
            #report-content-box {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
                background-color: white !important;
                box-shadow: none !important;
                border: none !important;
                padding: 20px;
            }
            #report-content-box h3 {
                font-size: 14pt !important;
            }
            #report-content-box .report-section-title {
                font-size: 13pt !important;
            }
        }
    </style>
</head>
<body>

    <div class="phone-frame">
        <div id="toast-container">Mensagem</div>

        <div class="screen" id="app-screen">
            
            <div class="app-brand-header">
                <h1>Pesquisa Justa</h1>
                <p>Sistema de Opinião Pública & Eleitoral</p>
            </div>

            <div class="status-banner" id="status-banner-text">
                🗳️ Pesquisa Eleitoral Oficial (1º Turno)
            </div>

            <div class="tse-notice-box">
                <span>📜 CONFORMIDADE ELEITORAL & REGISTRO TSE</span>
                <p>Protocolo PesqEle: BR-02849/2026 | Resolução TSE nº 23.600/2019</p>
            </div>

            <div class="screen-content">
                <!-- TELA 1: CADASTRO DEMOGRÁFICO DO ELEITOR -->
                <div id="screen-register" class="view">
                    <div style="text-align: center; margin-bottom: 6px;">
                        <h1 class="header-title">Perfil Demográfico</h1>
                        <p class="subtitle">Dados obrigatórios para ponderação estatística oficial (IBGE / TSE).</p>
                    </div>
                    
                    <!-- LINHA 1: WHATSAPP E NASCIMENTO -->
                    <div class="form-row">
                        <div class="form-group" style="flex: 1.1;">
                            <label>(DDD) WhatsApp</label>
                            <input type="tel" id="whatsapp-input" placeholder="(92) 99999-9999" maxlength="15" inputmode="numeric" oninput="autoMaskPhone(this)" onblur="autoMaskPhone(this)">
                        </div>
                        <div class="form-group" style="flex: 0.9;">
                            <label>Nascimento</label>
                            <input type="tel" id="birthdate-input" placeholder="DD/MM/AAAA" maxlength="10" inputmode="numeric" oninput="autoMaskDate(this)" onblur="autoMaskDate(this)">
                        </div>
                    </div>

                    <!-- LINHA 2: ESTADO E MUNICÍPIO -->
                    <div class="form-row">
                        <div class="form-group" style="flex: 0.9;">
                            <label>Estado / UF</label>
                            <select id="state-input" onchange="updateCitySuggestions()">
                                <option value="">Selecione UF</option>
                                <option value="AC">Acre - AC</option>
                                <option value="AL">Alagoas - AL</option>
                                <option value="AP">Amapá - AP</option>
                                <option value="AM" selected>Amazonas - AM</option>
                                <option value="BA">Bahia - BA</option>
                                <option value="CE">Ceará - CE</option>
                                <option value="DF">Distrito Federal - DF</option>
                                <option value="ES">Espírito Santo - ES</option>
                                <option value="GO">Goiás - GO</option>
                                <option value="MA">Maranhão - MA</option>
                                <option value="MT">Mato Grosso - MT</option>
                                <option value="MS">Mato Grosso do Sul - MS</option>
                                <option value="MG">Minas Gerais - MG</option>
                                <option value="PA">Pará - PA</option>
                                <option value="PB">Paraíba - PB</option>
                                <option value="PR">Paraná - PR</option>
                                <option value="PE">Pernambuco - PE</option>
                                <option value="PI">Piauí - PI</option>
                                <option value="RJ">Rio de Janeiro - RJ</option>
                                <option value="RN">Rio Grande do Norte - RN</option>
                                <option value="RS">Rio Grande do Sul - RS</option>
                                <option value="RO">Rondônia - RO</option>
                                <option value="RR">Roraima - RR</option>
                                <option value="SC">Santa Catarina - SC</option>
                                <option value="SP">São Paulo - SP</option>
                                <option value="SE">Sergipe - SE</option>
                                <option value="TO">Tocantins - TO</option>
                                <option value="ZZ">🌎 Outros Países (Exterior)</option>
                            </select>
                        </div>
                        <div class="form-group" style="flex: 1.1;">
                            <label id="city-label-text">Município / Capital</label>
                            <input type="text" id="city-input" placeholder="Digite a cidade..." value="Manaus">
                        </div>
                    </div>

                    <!-- LINHA 3: ZONA E ESCOLARIDADE -->
                    <div class="form-row">
                        <div class="form-group" style="flex: 1;">
                            <label>Zona / Região</label>
                            <select id="zone-input">
                                <option value="">Selecione...</option>
                                <option value="Zona Norte">Zona Norte</option>
                                <option value="Zona Sul" selected>Zona Sul</option>
                                <option value="Zona Leste">Zona Leste</option>
                                <option value="Zona Oeste">Zona Oeste</option>
                                <option value="Zona Centro-Oeste">Zona Centro-Oeste</option>
                                <option value="Zona Centro-Sul">Zona Centro-Sul</option>
                                <option value="Zona Central / Centro">Zona Central / Centro</option>
                                <option value="Zona Urbana">Zona Urbana</option>
                                <option value="Zona Rural / Distritos">Zona Rural / Distritos</option>
                                <option value="Seção Consular / Exterior">Exterior</option>
                            </select>
                        </div>
                        <div class="form-group" style="flex: 1;">
                            <label>Escolaridade</label>
                            <select id="education-input">
                                <option value="">Selecione...</option>
                                <option value="Sem Instrução">Sem Instrução</option>
                                <option value="Fund. Incompleto">Fund. Incompl.</option>
                                <option value="Fund. Completo">Fund. Compl.</option>
                                <option value="Médio Incompleto">Médio Incompl.</option>
                                <option value="Médio Completo">Médio Compl.</option>
                                <option value="Superior Incompleto">Superior Incompl.</option>
                                <option value="Superior Completo">Superior Compl.</option>
                                <option value="Pós-Graduação" selected>Pós-Graduação</option>
                                <option value="Mestrado">Mestrado</option>
                                <option value="Doutorado">Doutorado</option>
                            </select>
                        </div>
                    </div>

                    <!-- LINHA 4: RENDA, GÊNERO E COR / RAÇA (IBGE) -->
                    <div class="form-row">
                        <div class="form-group" style="flex: 1;">
                            <label>Renda Familiar</label>
                            <select id="income-input">
                                <option value="">Salários Mínimos</option>
                                <option value="1">Até 1 S.M.</option>
                                <option value="3">1 a 3 S.M.</option>
                                <option value="5">3 a 5 S.M.</option>
                                <option value="10" selected>5 a 10 S.M.</option>
                                <option value="11">Acima de 10 S.M.</option>
                            </select>
                        </div>
                        <div class="form-group" style="flex: 1;">
                            <label>Gênero</label>
                            <select id="gender-input">
                                <option value="">Selecione...</option>
                                <option value="Masculino">Masculino</option>
                                <option value="Feminino">Feminino</option>
                                <option value="LGBTQIA+" selected>LGBTQIA+</option>
                                <option value="Outro">Outro</option>
                            </select>
                        </div>
                        <div class="form-group" style="flex: 1;">
                            <label>Cor / Raça (IBGE)</label>
                            <select id="race-input">
                                <option value="">Selecione...</option>
                                <option value="Branca">Branca</option>
                                <option value="Preta">Preta</option>
                                <option value="Parda">Parda</option>
                                <option value="Amarela">Amarela</option>
                                <option value="Indígena" selected>Indígena</option>
                            </select>
                        </div>
                    </div>

                    <div class="checkbox-group">
                        <input type="checkbox" id="lgpd-check" checked>
                        <label for="lgpd-check" style="color: var(--text-main); font-size: 0.50rem; cursor: pointer; text-align: left;">Autorizo o uso destes dados para fins estatísticos e anonimização conforme LGPD e TSE.</label>
                    </div>

                    <button onclick="goToAuth()">Prosseguir para Autenticação</button>
                    
                    <div style="display: flex; gap: 6px; margin-top: 6px;">
                        <button onclick="openAdminLogin()" style="flex: 1; background-color: #090d16; border: 1px dashed var(--border); color: var(--text-muted); font-size: 0.50rem;">🔒 Acesso Gestor (ADM)</button>
                        <button onclick="openMediaLogin()" style="flex: 1; background-color: #090d16; border: 1px dashed #10b981; color: #10b981; font-size: 0.50rem;">📰 Acesso Mídia / Imprensa</button>
                    </div>
                </div>

                <!-- TELA 1.1: LOGIN ADM -->
                <div id="screen-admin-login" class="view hidden">
                    <div style="text-align: center; margin-bottom: 6px;">
                        <span class="badge" style="background-color: rgba(56, 189, 248, 0.2); color: #38bdf8;">Painel de Controle</span>
                        <h1 class="header-title">Autenticação do Gestor</h1>
                        <p class="subtitle">Insira a chave mestra do sistema para acessar a retaguarda analítica.</p>
                    </div>

                    <div class="form-group" style="margin-bottom: 8px;">
                        <label>Configurar Turno Ativo do Sistema</label>
                        <select id="admin-turn-toggle" onchange="toggleSystemTurn()">
                            <option value="1">1º Turno (Fase Inicial)</option>
                            <option value="2">2º Turno (Fase Final / Desempate)</option>
                        </select>
                    </div>

                    <div class="form-group" style="margin-bottom: 8px;">
                        <label>Chave de Acesso ADM</label>
                        <input type="password" id="admin-pass-input" placeholder="Digite a senha (ex: adm2026)">
                    </div>
                    <button onclick="validateAdminLogin()" style="background-color: var(--accent); border-color: #14b8a6;">Entrar no Painel Macro</button>
                    <button onclick="backToRegister()" style="background-color: #334155;">Voltar ao Início</button>
                </div>

                <!-- TELA 1.2: LOGIN MÍDIA / IMPRENSA -->
                <div id="screen-media-login" class="view hidden">
                    <div style="text-align: center; margin-bottom: 6px;">
                        <span class="badge" style="background-color: rgba(16, 185, 129, 0.2); color: #10b981;">Licenciamento Comercial</span>
                        <h1 class="header-title">Portal de Imprensa & Mídia</h1>
                        <p class="subtitle">Informe sua Chave de Licença Contratada para acessar os relatórios executivos.</p>
                    </div>

                    <div class="form-group" style="margin-bottom: 8px;">
                        <label>Chave de Licença Comercial</label>
                        <input type="text" id="media-key-input" placeholder="Ex: TV-AM-2026, BLOG-MANAUS, JORNAL-2026" style="text-transform: uppercase;">
                    </div>
                    
                    <div style="background-color: #090d16; border: 1px solid var(--border); padding: 6px; border-radius: 6px; margin-bottom: 8px; font-size: 0.50rem; color: var(--text-muted); text-align: center;">
                        💡 <em>A chave de acesso define o cabeçalho comercial do veículo nos documentos gerados.</em>
                    </div>

                    <button onclick="validateMediaLogin()" style="background-color: #10b981; border-color: #059669;">Acessar Painel de Relatórios</button>
                    <button onclick="backToRegisterFromMedia()" style="background-color: #334155;">Voltar ao Início</button>
                </div>

                <!-- TELA 2: AUTENTICAÇÃO -->
                <div id="screen-auth" class="view hidden">
                    <div style="text-align: center;">
                        <span class="badge">Segurança & Acesso</span>
                        <h1 class="header-title">Validação por Padrão de Pontos</h1>
                        <p class="subtitle">Desenhe seu padrão de segurança ou use a biometria para confirmar acesso.</p>
                    </div>

                    <div class="pattern-lock-container" id="pattern-grid">
                        <div class="pattern-dot" data-id="1" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="2" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="3" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="4" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="5" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="6" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="7" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="8" onclick="toggleDot(this)"></div>
                        <div class="pattern-dot" data-id="9" onclick="toggleDot(this)"></div>
                    </div>

                    <p style="text-align: center; font-size: 0.52rem; color: var(--text-muted); margin: 0;">Toque em pelo menos 3 pontos para criar seu padrão ou clique em biometria.</p>

                    <button onclick="startVoting(event)" style="background-color: #0f766e; border-color: #14b8a6;">Confirmar Padrão e Acessar Urna</button>
                    <button onclick="simulateBiometric()" style="background-color: #334155;">👆 Usar Biometria Facial / Digital</button>
                </div>

                <!-- TELA 3: CÉDULA DE VOTAÇÃO -->
                <div id="screen-voting" class="view hidden">
                    <div style="text-align: center;">
                        <span class="badge" id="voting-badge">Etapa 1 de X</span>
                        <h2 id="voting-title" style="font-size: 0.85rem;">Cargo</h2>
                        <p class="subtitle" id="voting-subtitle">Selecione 1 opção</p>
                    </div>

                    <div id="candidates-container"></div>

                    <div class="special-votes-wrapper">
                        <div class="special-vote-btn" onclick="handleSpecialVote('Votos Brancos', event)">Branco</div>
                        <div class="special-vote-btn" onclick="handleSpecialVote('Votos Nulos', event)">Nulo</div>
                        <div class="special-vote-btn" onclick="handleSpecialVote('Indecisos / Não Sabe', event)">Indeciso</div>
                    </div>

                    <button id="btn-next-vote" onclick="nextVotingStep()" style="background-color: #0f766e; border-color: #14b8a6;" disabled>Confirmar e Avançar</button>
                </div>

                <!-- TELA 4: SUCESSO -->
                <div id="screen-success" class="view hidden success-box">
                    <div class="success-icon">🛡️</div>
                    <h2 style="color: #10b981; font-size: 0.85rem;">Voto Computado e Anonimizado</h2>
                    <p class="subtitle">Seu voto foi segregado em urna cega. O histórico foi apagado deste dispositivo.</p>
                    <div style="background-color: #090d16; padding: 6px; border-radius: 6px; border: 1px solid var(--border); margin: 8px 0;">
                        <p style="font-size: 0.52rem; margin: 0; color: var(--text-muted);">Status: <strong style="color: var(--text-main);">Acesso encerrado para esta consulta.</strong></p>
                    </div>
                    <button onclick="goToResults()">Consultar Resultados e Ficha TSE</button>
                </div>

                <!-- TELA 5: RESULTADOS / PAINEL ANALÍTICO ADM -->
                <div id="screen-results" class="view hidden">
                    <div style="display: flex; gap: 6px; margin-bottom: 6px;">
                        <div class="admin-stat-card" style="flex: 1;">
                            <h3 id="stat-total-votes">4.500</h3>
                            <p>Amostra Consolidada</p>
                        </div>
                        <div class="admin-stat-card" style="flex: 1;">
                            <h3 style="color: #10b981;">99.8%</h3>
                            <p>Integridade Blindada</p>
                        </div>
                    </div>

                    <div class="result-tabs" id="result-tabs-container"></div>

                    <div class="filter-box">
                        <div style="display: flex; gap: 6px; margin-bottom: 4px;">
                            <label style="flex: 1; font-size: 0.52rem; color: var(--text-muted); font-weight: bold;">Estado / Países:</label>
                            <label id="filter-second-label" style="flex: 1; font-size: 0.52rem; color: var(--text-muted); font-weight: bold;">Município / Países:</label>
                        </div>

                        <div style="display: flex; gap: 6px; margin-bottom: 6px;" id="geographic-selectors-wrapper">
                            <select id="filter-state-select" onchange="onStateFilterChange()" style="flex: 1; font-size: 0.52rem; padding: 5px;">
                                <option value="AM">Amazonas - AM</option>
                                <option value="AC">Acre - AC</option>
                                <option value="AL">Alagoas - AL</option>
                                <option value="AP">Amapá - AP</option>
                                <option value="BA">Bahia - BA</option>
                                <option value="CE">Ceará - CE</option>
                                <option value="DF">Distrito Federal - DF</option>
                                <option value="ES">Espírito Santo - ES</option>
                                <option value="GO">Goiás - GO</option>
                                <option value="MA">Maranhão - MA</option>
                                <option value="MT">Mato Grosso - MT</option>
                                <option value="MS">Mato Grosso do Sul - MS</option>
                                <option value="MG">Minas Gerais - MG</option>
                                <option value="PA">Pará - PA</option>
                                <option value="PB">Paraíba - PB</option>
                                <option value="PR">Paraná - PR</option>
                                <option value="PE">Pernambuco - PE</option>
                                <option value="PI">Piauí - PI</option>
                                <option value="RJ">Rio de Janeiro - RJ</option>
                                <option value="RN">Rio Grande do Norte - RN</option>
                                <option value="RS">Rio Grande do Sul - RS</option>
                                <option value="RO">Rondônia - RO</option>
                                <option value="RR">Roraima - RR</option>
                                <option value="SC">Santa Catarina - SC</option>
                                <option value="SP">São Paulo - SP</option>
                                <option value="SE">Sergipe - SE</option>
                                <option value="TO">Tocantins - TO</option>
                                <option value="ZZ">🌎 Outros Países (Exterior)</option>
                            </select>
                            
                            <input type="text" id="filter-city-select" oninput="onCityFilterChange()" placeholder="Digite a cidade..." value="Manaus" style="flex: 1; font-size: 0.52rem; padding: 5px;">
                        </div>

                        <label id="macro-label" style="margin-bottom: 2px; color: var(--text-main); font-weight: bold; font-size: 0.52rem;">Recorte Geográfico:</label>
                        <div id="macro-filters-container" class="sub-filters" style="margin-bottom: 4px;"></div>
                        <div id="section-divider-elem" class="section-divider">📍 Zonas da Cidade Selecionada</div>
                        <div id="micro-filters-container" class="sub-filters"></div>
                    </div>

                    <div class="mode-toggle">
                        <button class="mode-btn active" id="btn-mode-geral" onclick="setCalculationMode('geral')">Intenção Geral (Amostra)</button>
                        <button class="mode-btn" id="btn-mode-validos" onclick="setCalculationMode('validos')">Votos Válidos (100% expurgado)</button>
                    </div>

                    <div id="results-content-container"></div>

                    <button onclick="openExportReport()" style="background-color: #0f766e; border-color: #14b8a6; font-size: 0.60rem; margin-top: 8px;">📄 Gerar Relatório Oficial Segmentado</button>

                    <div style="background-color: #090d16; padding: 6px; border-radius: 6px; border: 1px solid var(--border); font-size: 0.50rem; color: var(--text-muted); line-height: 1.2; margin-top: 6px;">
                        <strong style="color: var(--text-main); display: block; margin-bottom: 2px;">Compliance (TSE):</strong>
                        • Protocolo PesqEle: BR-02849/2026 | Amostra: 4.500 Ponderados | Margem: ± 1.5%
                    </div>

                    <button onclick="resetApp()" style="padding: 6px; background-color: #334155; font-size: 0.52rem; margin-top: 6px;">Sair / Reiniciar Teste</button>
                </div>

                <!-- TELA 6: MÓDULO INTERATIVO DE RELATÓRIO OFICIAL -->
                <div id="screen-export" class="view hidden" style="flex: 1; display: flex; flex-direction: column;">
                    
                    <div style="text-align: center; margin-bottom: 6px;">
                        <span class="badge" style="background-color: rgba(16, 185, 129, 0.2); color: #10b981;">Gerador Analítico</span>
                        <h2 style="font-size: 0.78rem; margin-bottom: 2px;">Documento Executivo de Imprensa</h2>
                    </div>

                    <div class="result-tabs" id="report-cargo-tabs">
                        <button class="tab-btn active" onclick="switchReportCargo('Presidente', this)">Presidente</button>
                        <button class="tab-btn" onclick="switchReportCargo('Governador', this)">Governador</button>
                        <button class="tab-btn" onclick="switchReportCargo('Senador', this)">Senador</button>
                        <button class="tab-btn" onclick="switchReportCargo('Prefeito', this)">Prefeito</button>
                    </div>

                    <div id="report-dynamic-filters" style="display: flex; gap: 6px; margin-bottom: 6px;"></div>

                    <div class="report-preview-box" id="report-content-box"></div>

                    <div style="margin-top: auto; display: flex; flex-direction: column; gap: 6px;">
                        <div style="display: flex; gap: 6px; margin-top: 6px;">
                            <button onclick="copyReportText()" style="flex: 1; background-color: #2563eb; border-color: #3b82f6; font-size: 0.52rem; padding: 7px 4px;">📋 Copiar</button>
                            <button onclick="toggleShareMenu()" style="flex: 1; background-color: #10b981; border-color: #059669; font-size: 0.52rem; padding: 7px 4px;">📤 Enviar</button>
                            <button onclick="printReport()" style="flex: 1; background-color: #2563eb; border-color: #3b82f6; font-size: 0.52rem; padding: 7px 4px;">🖨️ Imprimir</button>
                        </div>

                        <div id="share-submenu" class="hidden" style="display: flex; gap: 6px; background-color: #1e293b; padding: 6px; border-radius: 6px; border: 1px dashed var(--border);">
                            <button onclick="shareWhatsApp()" style="flex: 1; background-color: #10b981; border-color: #059669; font-size: 0.52rem; padding: 6px 4px;">💬 WhatsApp</button>
                            <button onclick="shareEmail()" style="flex: 1; background-color: #475569; border-color: #64748b; font-size: 0.52rem; padding: 6px 4px;">📧 E-mail</button>
                        </div>
                        
                        <button onclick="downloadReportPdf()" style="background-color: #0f766e; border-color: #14b8a6; font-size: 0.60rem;">💾 Salvar Arquivo (PDF)</button>
                        <button onclick="backToResults()" style="background-color: #334155; font-size: 0.58rem;">Voltar ao Painel Analítico</button>
                    </div>
                </div>
            </div>

            <div class="external-sponsor-banner" id="external-sponsor-container">
                <span>Patrocínio Institucional / Comercial</span>
                <p>🏢 Anúncio Comercial Genérico ou Apoio Tecnológico 2026</p>
            </div>

        </div>
    </div>

    <script>
        let currentYear = 2026;
        let currentTurn = 1; 
        let currentStep = 0;
        let activeBallots = [];
        let votesData = {};
        let currentMode = 'geral'; 
        let lastLoadedCategory = '';
        let lastLoadedKey = '';
        let selectedPattern = [];
        let activeMediaInfo = null;

        const demoMediaKeys = {
            'TV-AM-2026': { name: 'Rede Amazônica de Comunicação', type: 'Emissora de TV / Rádio', tier: 'Licenciamento Estadual' },
            'BLOG-MANAUS': { name: 'Portal & Blog de Notícias Manaus', type: 'Portal Eletrônico Local', tier: 'Licenciamento Municipal' },
            'JORNAL-2026': { name: 'Jornal Commercio do Amazonas', type: 'Jornal Impresso / Digital', tier: 'Licenciamento Estadual' },
            'MIDIA-NACIONAL': { name: 'Agência Nacional de Notícias', type: 'Veículo Nacional de Imprensa', tier: 'Licenciamento Nacional' }
        };

        const electionSchedules = {
            2026: {
                1: [
                    { id: 'president', title: "Presidente", subtitle: "Selecione 1 candidato ou voto especial", type: "single", candidates: [
                        { name: "Candidato Alpha", party: "PTX / Nº 12", img: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150" },
                        { name: "Candidato Beta", party: "PLZ / Nº 22", img: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150" }
                    ]},
                    { id: 'governor', title: "Governador", subtitle: "Selecione 1 candidato ou voto especial", type: "single", candidates: [
                        { name: "Candidato Delta", party: "PSB / Nº 40", img: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150" },
                        { name: "Candidato Ômega", party: "PSD / Nº 55", img: "https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?w=150" }
                    ]},
                    { id: 'senator', title: "Senador(es)", subtitle: "Selecione ATÉ 2 candidatos", type: "multiple", candidates: [
                        { name: "Candidato Um", party: "MDB / Nº 151", img: "https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?w=150" },
                        { name: "Candidato Dois", party: "UNIÃO / Nº 444", img: "https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?w=150" }
                    ]},
                    { id: 'mayor', title: "Prefeito", subtitle: "Selecione 1 candidato ou voto especial", type: "single", candidates: [
                        { name: "Candidato X", party: "UNIÃO / Nº 44", img: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=150" },
                        { name: "Candidato Y", party: "PSD / Nº 55", img: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150" }
                    ]}
                ],
                2: [
                    { id: 'president_2t', title: "Presidente", subtitle: "Finalistas - Selecione 1 candidato", type: "single", candidates: [
                        { name: "Candidato Alpha", party: "PTX / Nº 12", img: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150" },
                        { name: "Candidato Beta", party: "PLZ / Nº 22", img: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=150" }
                    ]},
                    { id: 'governor_2t', title: "Governador", subtitle: "Finalistas - Selecione 1 candidato", type: "single", candidates: [
                        { name: "Candidato Delta", party: "PSB / Nº 40", img: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=150" },
                        { name: "Candidato Ômega", party: "PSD / Nº 55", img: "https://images.unsplash.com/photo-1519085360753-af0119f7cbe7?w=150" }
                    ]},
                    { id: 'mayor_2t', title: "Prefeito", subtitle: "Finalistas Municipal", type: "single", candidates: [
                        { name: "Candidato X", party: "UNIÃO / Nº 44", img: "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=150" },
                        { name: "Candidato Y", party: "PSD / Nº 55", img: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=150" }
                    ]}
                ]
            }
        };

        const statesOptionsHTML = `
            <option value="AC">Acre - AC</option><option value="AL">Alagoas - AL</option><option value="AP">Amapá - AP</option>
            <option value="AM" selected>Amazonas - AM</option><option value="BA">Bahia - BA</option><option value="CE">Ceará - CE</option>
            <option value="DF">Distrito Federal - DF</option><option value="ES">Espírito Santo - ES</option><option value="GO">Goiás - GO</option>
            <option value="MA">Maranhão - MA</option><option value="MT">Mato Grosso - MT</option><option value="MS">Mato Grosso do Sul - MS</option>
            <option value="MG">Minas Gerais - MG</option><option value="PA">Pará - PA</option><option value="PB">Paraíba - PB</option>
            <option value="PR">Paraná - PR</option><option value="PE">Pernambuco - PE</option><option value="PI">Piauí - PI</option>
            <option value="RJ">Rio de Janeiro - RJ</option><option value="RN">Rio Grande do Norte - RN</option><option value="RS">Rio Grande do Sul - RS</option>
            <option value="RO">Rondônia - RO</option><option value="RR">Roraima - RR</option><option value="SC">Santa Catarina - SC</option>
            <option value="SP">São Paulo - SP</option><option value="SE">Sergipe - SE</option><option value="TO">Tocantins - TO</option>
        `;

        const zonesOptionsHTML = `
            <option value="Zona Norte">Zona Norte</option><option value="Zona Sul">Zona Sul</option>
            <option value="Zona Leste">Zona Leste</option><option value="Zona Oeste">Zona Oeste</option>
            <option value="Zona Centro-Oeste">Zona Centro-Oeste</option><option value="Zona Centro-Sul">Zona Centro-Sul</option>
            <option value="Zona Central / Centro">Zona Central / Centro</option><option value="Zona Rural / Distritos">Zona Rural / Distritos</option>
        `;

        const internationalCountryList = [
            "Todos os Países", "Estados Unidos (EUA)", "Portugal", "Japão", "Espanha", "Reino Unido", "França", "Itália", "Alemanha", "Argentina"
        ];

        /* FORMATADORES DE TECLADO AUTOMÁTICOS */
        function autoMaskPhone(input) {
            if (!input) return;
            let digits = input.value.replace(/\D/g, "");
            if (digits.length > 11) digits = digits.substring(0, 11);
            let formatted = "";
            if (digits.length > 0) {
                formatted = "(" + digits.substring(0, 2);
                if (digits.length > 2) {
                    formatted += ") " + digits.substring(2, 7);
                    if (digits.length > 7) formatted += "-" + digits.substring(7, 11);
                }
            }
            input.value = formatted;
        }

        function autoMaskDate(input) {
            if (!input) return;
            let digits = input.value.replace(/\D/g, "");
            if (digits.length > 8) digits = digits.substring(0, 8);
            let formatted = "";
            if (digits.length > 0) {
                formatted = digits.substring(0, 2);
                if (digits.length > 2) {
                    formatted += "/" + digits.substring(2, 4);
                    if (digits.length > 4) formatted += "/" + digits.substring(4, 8);
                }
            }
            input.value = formatted;
        }

        function updateSystemState() {
            activeBallots = electionSchedules[currentYear][currentTurn] || electionSchedules[2026][1];
            const bannerElem = document.getElementById('status-banner-text');
            if (bannerElem) bannerElem.innerText = `🗳️ Pesquisa Eleitoral Oficial (${currentTurn}º Turno)`;
        }
        updateSystemState();

        function showToast(message, isError = false) {
            const toast = document.getElementById('toast-container');
            if (!toast) return;
            toast.innerText = message;
            if(isError) toast.classList.add('error'); else toast.classList.remove('error');
            toast.classList.add('show');
            setTimeout(() => toast.classList.remove('show'), 3500);
        }

        function updateCitySuggestions() {
            const stateVal = document.getElementById('state-input').value;
            const cityLabel = document.getElementById('city-label-text');
            if(stateVal === 'ZZ') cityLabel.innerText = "🌎 País (Exterior)";
            else cityLabel.innerText = "Município / Capital";
        }

        function openAdminLogin() {
            document.getElementById('screen-register').classList.add('hidden');
            document.getElementById('screen-admin-login').classList.remove('hidden');
        }
        function backToRegister() {
            document.getElementById('screen-admin-login').classList.add('hidden');
            document.getElementById('screen-register').classList.remove('hidden');
        }

        function openMediaLogin() {
            document.getElementById('screen-register').classList.add('hidden');
            document.getElementById('screen-media-login').classList.remove('hidden');
        }
        function backToRegisterFromMedia() {
            document.getElementById('screen-media-login').classList.add('hidden');
            document.getElementById('screen-register').classList.remove('hidden');
        }

        function validateMediaLogin() {
            const key = document.getElementById('media-key-input').value.trim().toUpperCase();
            if(!key) { showToast('⚠️ Digite sua chave de licença de mídia.', true); return; }
            if(demoMediaKeys[key]) activeMediaInfo = demoMediaKeys[key];
            else activeMediaInfo = { name: `Veículo Mídia (${key})`, type: 'Portal / Veículo', tier: 'Licença Comercial' };
            document.getElementById('screen-media-login').classList.add('hidden');
            document.getElementById('screen-export').classList.remove('hidden');
            renderReportFilters();
            showToast(`📰 Licença ativada: ${activeMediaInfo.name}`);
        }

        function toggleSystemTurn() {
            currentTurn = parseInt(document.getElementById('admin-turn-toggle').value);
            updateSystemState();
        }

        function validateAdminLogin() {
            const pass = document.getElementById('admin-pass-input').value.trim();
            if(pass === 'adm2026' || pass === '') {
                activeMediaInfo = null;
                document.getElementById('screen-admin-login').classList.add('hidden');
                document.getElementById('screen-results').classList.remove('hidden');
                setupResultTabs();
                showToast('✅ Acesso ADM liberado!');
            } else showToast('❌ Chave incorreta. Tente "adm2026".', true);
        }
        
        /* AVANÇO GARANTIDO E SEM TRAVAS PARA QUALQUER CELULAR */
        function goToAuth() {
            const phoneInput = document.getElementById('whatsapp-input');
            const birthInput = document.getElementById('birthdate-input');
            autoMaskPhone(phoneInput);
            autoMaskDate(birthInput);

            const state = document.getElementById('state-input').value;
            const city = document.getElementById('city-input').value.trim();
            const lgpd = document.getElementById('lgpd-check').checked;

            if(!state) { showToast('⚠️ Selecione o Estado / UF.', true); return; }
            if(!city) { showToast('⚠️ Digite ou informe o Município.', true); return; }
            if(!lgpd) { showToast('⚠️ Marque o aceite do termo LGPD.', true); return; }

            activeMediaInfo = null;
            document.getElementById('screen-register').classList.add('hidden');
            document.getElementById('screen-auth').classList.remove('hidden');
        }

        function toggleDot(dotElement) {
            const id = dotElement.getAttribute('data-id');
            if(dotElement.classList.contains('active')) {
                dotElement.classList.remove('active');
                selectedPattern = selectedPattern.filter(item => item !== id);
            } else {
                dotElement.classList.add('active');
                selectedPattern.push(id);
            }
        }

        function simulateBiometric() {
            showToast('✅ Biometria confirmada!');
            setTimeout(() => startVoting(), 600);
        }

        function startVoting(event) {
            if(selectedPattern.length < 3 && event && event.currentTarget && event.currentTarget.innerText.includes('Padrão')) {
                showToast('⚠️ Selecione ao menos 3 pontos no padrão.', true); return;
            }
            document.getElementById('screen-auth').classList.add('hidden');
            document.getElementById('screen-voting').classList.remove('hidden');
            currentStep = 0;
            renderBallot();
        }

        let currentSelections = [];
        function renderBallot() {
            updateSystemState();
            const data = activeBallots[currentStep];
            document.getElementById('voting-badge').innerText = `Etapa ${currentStep + 1} de ${activeBallots.length} (${currentTurn}º Turno)`;
            document.getElementById('voting-title').innerText = data.title;
            document.getElementById('voting-subtitle').innerText = data.subtitle;

            const container = document.getElementById('candidates-container');
            container.innerHTML = '';
            data.candidates.forEach((cand) => {
                const card = document.createElement('div'); card.className = 'candidate-card';
                card.innerHTML = `<img src="${cand.img}" class="candidate-img"><div class="candidate-info"><h4>${cand.name}</h4><p>${cand.party}</p></div>`;
                card.onclick = () => handleSelect(card, cand.name, data.type);
                container.appendChild(card);
            });
            document.getElementById('btn-next-vote').disabled = true;
            currentSelections = [];
        }

        function handleSelect(cardElement, name, type) {
            document.querySelectorAll('.special-vote-btn').forEach(b => b.classList.remove('selected'));
            if(type === 'single') {
                document.querySelectorAll('.candidate-card').forEach(c => c.classList.remove('selected'));
                cardElement.classList.add('selected'); currentSelections = [name];
                document.getElementById('btn-next-vote').disabled = false;
            } else {
                if(cardElement.classList.contains('selected')) {
                    cardElement.classList.remove('selected'); currentSelections = currentSelections.filter(item => item !== name);
                } else {
                    if(currentSelections.length < 2) { cardElement.classList.add('selected'); currentSelections.push(name); }
                    else showToast('⚠️ Selecione no máximo 2 candidatos.', true);
                }
                document.getElementById('btn-next-vote').disabled = currentSelections.length === 0;
            }
        }

        function handleSpecialVote(type, event) {
            document.querySelectorAll('.candidate-card').forEach(c => c.classList.remove('selected'));
            document.querySelectorAll('.special-vote-btn').forEach(b => b.classList.remove('selected'));
            if(event && event.currentTarget) event.currentTarget.classList.add('selected');
            currentSelections = [type];
            document.getElementById('btn-next-vote').disabled = false;
        }

        function nextVotingStep() {
            updateSystemState();
            const currentBallotMeta = activeBallots[currentStep];
            votesData[currentBallotMeta.id] = [...currentSelections];
            currentSelections = [];
            currentStep++;
            if(currentStep < activeBallots.length) renderBallot();
            else {
                document.getElementById('screen-voting').classList.add('hidden');
                document.getElementById('screen-success').classList.remove('hidden');
            }
        }

        function goToResults() {
            document.getElementById('screen-success').classList.add('hidden');
            document.getElementById('screen-results').classList.remove('hidden');
            setupResultTabs();
        }

        const hierarchicalData = {
            president: { datasets: { "Geral do País": [ { name: "Candidato Alpha", percent: 42.0 }, { name: "Candidato Beta", percent: 36.0 }, { name: "Votos Brancos", percent: 6.0, color: "#64748b" }, { name: "Votos Nulos", percent: 5.0, color: "#475569" }, { name: "Indecisos / Não Sabe", percent: 11.0, color: "#334155" } ] } },
            governor: { datasets: { "Geral Estado": [ { name: "Candidato Delta", percent: 48.0 }, { name: "Candidato Ômega", percent: 32.0 }, { name: "Votos Brancos", percent: 6.0, color: "#64748b" }, { name: "Votos Nulos", percent: 5.0, color: "#475569" }, { name: "Indecisos / Não Sabe", percent: 9.0, color: "#334155" } ] } },
            mayor: { datasets: { "Geral da Capital": [ { name: "Candidato X", percent: 46.0 }, { name: "Candidato Y", percent: 40.0 }, { name: "Votos Brancos", percent: 5.0, color: "#64748b" }, { name: "Votos Nulos", percent: 5.0, color: "#475569" }, { name: "Indecisos / Não Sabe", percent: 5.0, color: "#334155" } ] } }
        };
        const presidentFilters = ["Geral do País", "Região Norte", "Região Nordeste", "Região Centro-Oeste", "Região Sudeste", "Região Sul"];
        const macroStateFilters = ["Geral Estado", "Geral da Capital", "Geral do Interior"];

        function setupResultTabs() {
            const tabsContainer = document.getElementById('result-tabs-container'); tabsContainer.innerHTML = '';
            activeBallots.forEach((ballot, index) => {
                const tabBtn = document.createElement('button'); tabBtn.className = `tab-btn ${index === 0 ? 'active' : ''}`;
                tabBtn.innerText = ballot.title;
                tabBtn.onclick = (e) => switchResultTab(ballot.id, e.currentTarget);
                tabsContainer.appendChild(tabBtn);
            });
            switchResultTab(activeBallots[0].id, tabsContainer.querySelector('.tab-btn'));
        }

        function switchResultTab(category, btnElement) {
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active')); btnElement.classList.add('active');
            lastLoadedCategory = category;
            const stateSelect = document.getElementById('filter-state-select');
            let sHTML = `<option value="">Selecione UF</option>${statesOptionsHTML}`;
            if(category === 'president' || category === 'president_2t') sHTML += `<option value="ZZ">🌎 Outros Países (Exterior)</option>`;
            stateSelect.innerHTML = sHTML;
            stateSelect.value = 'AM';
            onStateFilterChange();
        }

        function onStateFilterChange() {
            const stateVal = document.getElementById('filter-state-select').value;
            const secondLabel = document.getElementById('filter-second-label');
            if(stateVal === 'ZZ') secondLabel.innerText = "Países:";
            else secondLabel.innerText = "Município / Países:";
            renderFilterSections();
        }

        function onCityFilterChange() { renderFilterSections(); }

        function renderFilterSections() {
            const macroContainer = document.getElementById('macro-filters-container'); 
            const microContainer = document.getElementById('micro-filters-container');
            const dividerElem = document.getElementById('section-divider-elem'); 
            const macroLabel = document.getElementById('macro-label');
            macroContainer.innerHTML = ''; microContainer.innerHTML = '';
            
            const stateVal = document.getElementById('filter-state-select').value;
            if(lastLoadedCategory === 'president' || lastLoadedCategory === 'president_2t') {
                dividerElem.style.display = 'none'; macroLabel.style.display = 'block'; macroLabel.innerText = "Recorte Geográfico (Federal):";
                if(stateVal === 'ZZ') { lastLoadedKey = "Outros Países"; renderSimulatedDataset(lastLoadedCategory, "Outros Países"); macroLabel.style.display = 'none'; } 
                else {
                    presidentFilters.forEach((f, i) => {
                        const b = document.createElement('button'); b.className = `sub-filter-btn ${i===0?'active':''}`; b.innerText = f;
                        b.onclick = (e) => { document.querySelectorAll('.sub-filter-btn').forEach(x=>x.classList.remove('active')); e.currentTarget.classList.add('active'); lastLoadedKey = f; renderSimulatedDataset(lastLoadedCategory, f); };
                        macroContainer.appendChild(b);
                    });
                    lastLoadedKey = presidentFilters[0]; renderSimulatedDataset(lastLoadedCategory, presidentFilters[0]);
                }
            } else {
                dividerElem.style.display = 'block'; macroLabel.style.display = 'block'; macroLabel.innerText = "Recorte Geográfico:";
                macroStateFilters.forEach((f, i) => {
                    const b = document.createElement('button'); b.className = `sub-filter-btn ${i===0?'active':''}`; b.innerText = f;
                    b.onclick = (e) => { document.querySelectorAll('.sub-filter-btn').forEach(x=>x.classList.remove('active')); e.currentTarget.classList.add('active'); lastLoadedKey = f; renderSimulatedDataset(lastLoadedCategory, f); };
                    macroContainer.appendChild(b);
                });
                lastLoadedKey = macroStateFilters[0]; renderSimulatedDataset(lastLoadedCategory, macroStateFilters[0]);
            }
        }

        function setCalculationMode(mode) {
            currentMode = mode;
            document.getElementById('btn-mode-geral').classList.toggle('active', mode === 'geral');
            document.getElementById('btn-mode-validos').classList.toggle('active', mode === 'validos');
            renderSimulatedDataset(lastLoadedCategory, lastLoadedKey);
        }

        function renderSimulatedDataset(category, filterKey) {
            lastLoadedKey = filterKey;
            let dataset = []; const config = hierarchicalData[category] || hierarchicalData['mayor'];
            if(config && config.datasets && config.datasets[filterKey]) dataset = JSON.parse(JSON.stringify(config.datasets[filterKey]));
            else dataset = [ { name: `Candidato Principal`, percent: 45.0 }, { name: `Candidato Opositor`, percent: 35.0 }, { name: "Votos Brancos", percent: 6.0, color: "#64748b" }, { name: "Votos Nulos", percent: 5.0, color: "#475569" }, { name: "Indecisos", percent: 9.0, color: "#334155" } ];
            
            if(currentMode === 'validos') {
                let validCandidates = dataset.filter(item => !item.name.toLowerCase().includes('branco') && !item.name.toLowerCase().includes('nulo') && !item.name.toLowerCase().includes('indeciso'));
                let somaValidos = validCandidates.reduce((acc, curr) => acc + curr.percent, 0);
                dataset = dataset.map(item => {
                    if(!item.name.toLowerCase().includes('branco') && !item.name.toLowerCase().includes('nulo') && !item.name.toLowerCase().includes('indeciso')) {
                        return { ...item, percent: parseFloat((somaValidos>0 ? (item.percent/somaValidos)*100 : 0).toFixed(1)) };
                    } else return { ...item, percent: 0, hidden: true };
                }).filter(item => !item.hidden);
            }

            const container = document.getElementById('results-content-container'); container.innerHTML = '';
            dataset.forEach(item => {
                const barDiv = document.createElement('div'); barDiv.className = 'result-bar-container';
                barDiv.innerHTML = `<div class="result-meta"><span>${item.name}</span><strong>${item.percent}%</strong></div><div class="progress-bar"><div class="progress-fill" style="width: ${item.percent}%; ${item.color ? 'background-color:'+item.color : ''}"></div></div>`;
                container.appendChild(barDiv);
            });
        }

        let activeReportCargo = 'Presidente';

        function openExportReport() {
            document.getElementById('screen-results').classList.add('hidden');
            document.getElementById('screen-export').classList.remove('hidden');
            renderReportFilters(); 
        }

        function switchReportCargo(cargo, btnElement) {
            document.querySelectorAll('#report-cargo-tabs .tab-btn').forEach(b => b.classList.remove('active'));
            btnElement.classList.add('active');
            activeReportCargo = cargo;
            renderReportFilters();
        }

        function renderReportFilters() {
            const container = document.getElementById('report-dynamic-filters');
            container.innerHTML = '';

            if (activeReportCargo === 'Presidente') {
                container.innerHTML = `
                    <select id="rep-nivel" onchange="updateReportSubfilters()" style="flex: 1; padding: 5px; font-size: 0.52rem; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;">
                        <option value="Geral (Brasil)">Geral (Brasil)</option>
                        <option value="Por Região">Por Região</option>
                        <option value="Por Estado">Por Estado (UF)</option>
                        <option value="Por Capitais">Por Capitais</option>
                        <option value="Por Município">Por Município</option>
                        <option value="Exterior">Exterior</option>
                    </select>
                    <select id="rep-detalhe" onchange="generateDynamicReport()" style="flex: 1; padding: 5px; font-size: 0.52rem; display: none; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;"></select>
                `;
            } else if (activeReportCargo === 'Governador' || activeReportCargo === 'Senador') {
                container.innerHTML = `
                    <select id="rep-estado" onchange="generateDynamicReport()" style="flex: 1; padding: 5px; font-size: 0.52rem; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;">
                        ${statesOptionsHTML}
                    </select>
                    <select id="rep-nivel" onchange="updateReportSubfilters()" style="flex: 1; padding: 5px; font-size: 0.52rem; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;">
                        <option value="Geral (Estado)">Geral (Estado)</option>
                        <option value="Capital">Capital</option>
                        <option value="Zonas da Capital">Zonas da Capital</option>
                        <option value="Geral Interior">Geral Interior</option>
                    </select>
                `;
            } else if (activeReportCargo === 'Prefeito') {
                container.innerHTML = `
                    <select id="rep-estado" onchange="generateDynamicReport()" style="flex: 1; padding: 5px; font-size: 0.52rem; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;">
                        ${statesOptionsHTML}
                    </select>
                    <input type="text" id="rep-city" oninput="generateDynamicReport()" placeholder="Digite a cidade..." value="Manaus" style="flex: 1; padding: 5px; font-size: 0.52rem; background-color: #090d16; color: var(--text-main); border: 1px solid var(--border); border-radius: 4px;">
                `;
            }
            updateReportSubfilters();
        }

        function updateReportSubfilters() {
            if(activeReportCargo === 'Presidente') {
                const nivel = document.getElementById('rep-nivel').value;
                const detalhe = document.getElementById('rep-detalhe');
                detalhe.style.display = 'block';

                if(nivel === 'Geral (Brasil)' || nivel === 'Por Capitais') {
                    detalhe.style.display = 'none';
                } else if(nivel === 'Por Região') {
                    detalhe.innerHTML = '<option>Norte</option><option>Nordeste</option><option>Centro-Oeste</option><option>Sudeste</option><option>Sul</option>';
                } else if(nivel === 'Por Estado' || nivel === 'Por Município') {
                    detalhe.innerHTML = statesOptionsHTML;
                } else if(nivel === 'Exterior') {
                    let cHTML = ''; internationalCountryList.forEach(c => cHTML+=`<option>${c}</option>`);
                    detalhe.innerHTML = cHTML;
                }
            }
            generateDynamicReport();
        }

        function generateDynamicReport() {
            let filterDesc = "";
            let candA = 0, candB = 0;
            let candAName = "", candBName = "";
            
            if(activeReportCargo === 'Presidente') { 
                const nivel = document.getElementById('rep-nivel').value;
                const detalhe = document.getElementById('rep-detalhe') ? document.getElementById('rep-detalhe').value : '';
                filterDesc = `<li><strong>Abrangência:</strong> ${nivel} ${detalhe ? '- ' + detalhe : ''}</li>`;
                candA = 48.5; candB = 41.2; 
                candAName = "Candidato Alpha (PTX)"; candBName = "Candidato Beta (PLZ)";
            }
            else if(activeReportCargo === 'Governador') { 
                const estado = document.getElementById('rep-estado').value;
                filterDesc = `<li><strong>Estado (UF):</strong> ${estado}</li>`;
                candA = 51.0; candB = 38.0; 
                candAName = "Candidato Delta (PSB)"; candBName = "Candidato Ômega (PSD)";
            }
            else if(activeReportCargo === 'Senador') { 
                const estado = document.getElementById('rep-estado').value;
                filterDesc = `<li><strong>Estado (UF):</strong> ${estado}</li>`;
                candA = 34.0; candB = 28.0; 
                candAName = "Candidato Um (MDB)"; candBName = "Candidato Dois (UNIÃO)";
            }
            else if(activeReportCargo === 'Prefeito') { 
                const estado = document.getElementById('rep-estado').value;
                const cityElem = document.getElementById('rep-city');
                const city = cityElem ? cityElem.value : 'Manaus';
                filterDesc = `<li><strong>Estado (UF):</strong> ${estado}</li><li><strong>Município:</strong> ${city}</li>`;
                candA = 46.0; candB = 40.0; 
                candAName = "Candidato X (UNIÃO)"; candBName = "Candidato Y (PSD)";
            }

            const rest = (100 - candA - candB).toFixed(1);

            let mediaHeaderHTML = "";
            if (activeMediaInfo) {
                mediaHeaderHTML = `
                    <div style="background-color: rgba(16, 185, 129, 0.1); border: 1px solid #10b981; border-radius: 6px; padding: 6px; margin-bottom: 8px; text-align: center;">
                        <span style="font-size: 0.48rem; color: #059669; font-weight: bold; text-transform: uppercase; display: block;">🏢 DOCUMENTO LICENCIADO PARA IMPRENSA</span>
                        <strong style="font-size: 0.65rem; color: #0f172a;">${activeMediaInfo.name}</strong>
                        <span style="font-size: 0.50rem; color: #475569; display: block;">Segmento: ${activeMediaInfo.type} | Cobertura: ${activeMediaInfo.tier}</span>
                    </div>
                `;
            }

            let reportHTML = `
                ${mediaHeaderHTML}
                <h3>DOCUMENTO DE IMPRENSA & CONFORMIDADE</h3>
                <p style="text-align:center; font-size: 0.52rem; color: #64748b; margin-bottom: 6px;">Protocolo PesqEle: BR-02849/2026 | Turno: ${currentTurn}º</p>
                <hr>
                <div class="report-section-title">📊 CARGO ANALISADO: ${activeReportCargo.toUpperCase()}</div>
                
                <p style="font-size: 0.56rem; color: #334155; margin-bottom: 2px;"><strong>Filtros Aplicados:</strong></p>
                <ul style="margin: 0 0 6px 15px; padding:0; font-size: 0.54rem; color: #475569;">
                    ${filterDesc}
                </ul>
                
                <div style="background-color: #f8fafc; border: 1px solid #cbd5e1; padding: 6px; border-radius: 6px;">
                    <p style="margin-top: 2px;">• ${candAName}: <strong>${candA}%</strong></p>
                    <p>• ${candBName}: <strong>${candB}%</strong></p>
                    <p style="margin-bottom: 2px;">• Votos Brancos / Nulos / Indecisos: <strong>${rest}%</strong></p>
                </div>
                
                <p style="font-size: 0.48rem; color: #94a3b8; text-align: center; margin-top: 8px;">Amostra segmentada extraída oficialmente do sistema cego.</p>
            `;

            document.getElementById('report-content-box').innerHTML = reportHTML;
        }

        function copyReportText() {
            const reportText = document.getElementById('report-content-box').innerText;
            var textArea = document.createElement("textarea");
            textArea.value = reportText; textArea.style.position = "fixed"; textArea.style.opacity = "0";
            document.body.appendChild(textArea); textArea.focus(); textArea.select();
            try {
                var successful = document.execCommand('copy');
                if(successful) showToast('📋 Relatório copiado para a área de transferência!');
                else showToast('❌ Erro ao copiar.', true);
            } catch (err) { showToast('❌ O navegador bloqueou a cópia.', true); }
            document.body.removeChild(textArea);
        }

        function toggleShareMenu() {
            const menu = document.getElementById('share-submenu');
            if (menu.classList.contains('hidden')) menu.classList.remove('hidden');
            else menu.classList.add('hidden');
        }

        function shareWhatsApp() {
            const reportText = document.getElementById('report-content-box').innerText;
            const textToShare = encodeURIComponent(reportText);
            window.open(`https://api.whatsapp.com/send?text=${textToShare}`, '_blank');
            showToast('💬 Abrindo WhatsApp...');
            document.getElementById('share-submenu').classList.add('hidden');
        }

        function shareEmail() {
            const reportText = document.getElementById('report-content-box').innerText;
            const subject = encodeURIComponent(`Relatório Segmentado - ${activeReportCargo}`);
            const body = encodeURIComponent(reportText);
            window.location.href = `mailto:?subject=${subject}&body=${body}`;
            showToast('📧 Abrindo E-mail...');
            document.getElementById('share-submenu').classList.add('hidden');
        }

        function printReport() {
            showToast('🖨️ Preparando página de impressão...');
            setTimeout(() => window.print(), 800);
        }

        function downloadReportPdf() {
            showToast('📄 DICA: Na janela a seguir, mude o destino para "Salvar como PDF".');
            setTimeout(() => window.print(), 2000);
        }

        function backToResults() {
            document.getElementById('screen-export').classList.add('hidden');
            if(activeMediaInfo) document.getElementById('screen-register').classList.remove('hidden');
            else document.getElementById('screen-results').classList.remove('hidden');
            document.getElementById('share-submenu').classList.add('hidden');
        }

        function resetApp() {
            currentStep = 0; votesData = {}; selectedPattern = []; activeMediaInfo = null;
            document.querySelectorAll('.pattern-dot').forEach(d => d.classList.remove('active'));
            document.getElementById('screen-results').classList.add('hidden');
            document.getElementById('screen-export').classList.add('hidden');
            document.getElementById('screen-admin-login').classList.add('hidden');
            document.getElementById('screen-media-login').classList.add('hidden');
            document.getElementById('screen-auth').classList.add('hidden');
            document.getElementById('screen-success').classList.add('hidden');
            document.getElementById('screen-register').classList.remove('hidden');
        }
    </script>
</body>
</html>
