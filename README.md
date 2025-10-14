<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Diagnóstico Financeiro • ROD LIDER</title>
  <meta name="description" content="Diagnóstico rápido para identificar a melhor opção de crédito para seu projeto. Sem compromisso." />
  <style>
    :root{
      --bg:#f5f7fb;
      --card:#ffffff;
      --accent:#0b5bd7; /* azul RODLIDER */
      --accent-dark:#083e9a;
      --success:#16a34a;
      --muted:#6b7280;
      --maxw:1100px;
      --radius:14px;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    *{box-sizing:border-box}
    body{margin:0;background:var(--bg);color:#111;line-height:1.45;-webkit-font-smoothing:antialiased}
    .wrap{max-width:var(--maxw);margin:28px auto;padding:20px}
    .site{display:grid;grid-template-columns:1fr 360px;gap:20px}
    .card{background:var(--card);border-radius:var(--radius);box-shadow:0 6px 22px rgba(8,20,40,0.06);padding:26px}
    header.site-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
    .brand{display:flex;gap:12px;align-items:center}
    .logo{width:64px;height:64px;border-radius:10px;background:linear-gradient(135deg,var(--accent) 0%, #000 100%);display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700}
    h1{font-size:20px;margin:0}
    p.lead{margin:6px 0 0;color:var(--muted);font-size:14px}
    .cta-whats{background:linear-gradient(90deg,var(--success),#0ea5a0);color:#fff;padding:8px 12px;border-radius:8px;text-decoration:none;font-weight:600}
    /* Main */
    .wizard-viewport{min-height:380px;display:flex;flex-direction:column;justify-content:space-between}
    .step-header{margin-bottom:8px}
    .progress{font-size:13px;color:var(--muted);margin-bottom:6px}
    .question{font-size:20px;font-weight:700;margin:0 0 8px}
    .hint{color:var(--muted);font-size:13px;margin-bottom:12px}
    .cards{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
    .choice{background:#fff;border:1px solid #e6e9ef;padding:14px;border-radius:10px;text-align:left;cursor:pointer;transition:all .14s;box-shadow:none}
    .choice:hover{transform:translateY(-3px);box-shadow:0 8px 20px rgba(11,91,215,0.08)}
    .choice.active{border-color:var(--accent);background:linear-gradient(180deg,rgba(11,91,215,0.06),#fff)}
    .range-wrap{margin:10px 0}
    .range-value{font-weight:600;margin-top:6px}
    input[type="range"]{width:100%}
    form .input-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px}
    input[type=text], input[type=email]{padding:12px;border:1px solid #e6e9ef;border-radius:8px;font-size:14px}
    .buttons{display:flex;gap:8px;margin-top:16px}
    button.btn{padding:10px 14px;border-radius:10px;border:0;cursor:pointer;font-weight:600}
    button.ghost{background:#f3f4f6;color:#111}
    button.primary{background:var(--accent);color:#fff}
    button.success{background:var(--success);color:#fff}
    aside{height:100%}
    .aside-block{margin-bottom:16px}
    .small{font-size:13px;color:var(--muted)}
    footer.page-footer{text-align:center;color:var(--muted);font-size:13px;margin-top:18px}
    /* Responsive */
    @media(max-width:980px){
      .site{grid-template-columns:1fr;padding-bottom:18px}
      aside{order:2}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <div class="site">
      <!-- Main column -->
      <div>
        <div class="card">
          <header class="site-header">
            <div class="brand">
              <div class="logo">ROD</div>
              <div>
                <h1>ROD LIDER — Diagnóstico Financeiro</h1>
                <p class="lead">Descubra em minutos o melhor caminho para realizar seu projeto — sem compromisso.</p>
              </div>
            </div>
            <div>
              <a class="cta-whats" id="callNow" href="https://wa.me/5598984533013" target="_blank" rel="noopener">Chamar no WhatsApp</a>
            </div>
          </header>

          <div class="wizard-viewport" id="wizard">
            <div>
              <div class="progress" id="progressText">Passo 1 de 5</div>

              <!-- Step container -->
              <div id="stepArea">
                <!-- Step 1 -->
                <div class="step" data-step="1">
                  <h2 class="question">Qual é o seu principal objetivo nos próximos 12 meses?</h2>
                  <div class="hint">Escolha a opção que melhor descreve seu projeto.</div>
                  <div class="cards" id="choicesStep1">
                    <div class="choice" data-value="negocio">Investir no meu negócio</div>
                    <div class="choice" data-value="imovel">Comprar um imóvel</div>
                    <div class="choice" data-value="veiculo">Adquirir um veículo</div>
                    <div class="choice" data-value="rural">Investir no agronegócio</div>
                    <div class="choice" data-value="outro" style="grid-column:1 / -1">Outro projeto pessoal</div>
                  </div>
                </div>

                <!-- Step 2 (sub objetivo) -->
                <div class="step" data-step="2" style="display:none">
                  <h2 class="question">Detalhe um pouco mais — em qual área?</h2>
                  <div class="hint" id="hintSub">Escolha a alternativa que melhor encaixa.</div>
                  <div class="cards" id="choicesStep2"></div>
                </div>

                <!-- Step 3 (valor estimado) -->
                <div class="step" data-step="3" style="display:none">
                  <h2 class="question">Qual o valor aproximado do projeto?</h2>
                  <div class="hint">Use o controle para indicar o valor total estimado.</div>
                  <div class="range-wrap">
                    <input type="range" id="valorRange" min="10000" max="1000000" step="1000" value="50000">
                    <div class="range-value">Valor estimado: <span id="valorText">R$ 50.000</span></div>
                  </div>
                </div>

                <!-- Step 4 (parcela confortável) -->
                <div class="step" data-step="4" style="display:none">
                  <h2 class="question">Qual parcela mensal cabe no seu orçamento?</h2>
                  <div class="hint">Arraste para indicar o valor mensal confortável.</div>
                  <div class="range-wrap">
                    <input type="range" id="parcelaRange" min="200" max="10000" step="50" value="1000">
                    <div class="range-value">Parcela confortável: <span id="parcelaText">R$ 1.000</span></div>
                  </div>
                </div>

                <!-- Step 5 (contato) -->
                <div class="step" data-step="5" style="display:none">
                  <h2 class="question">Quase lá — compartilhe seus dados</h2>
                  <div class="hint">Para receber sua análise personalizada e contato do Daniel.</div>

                  <form id="leadForm" onsubmit="return false;">
                    <div class="input-grid">
                      <input type="text" id="nome" placeholder="Nome completo" required />
                      <input type="text" id="whats" placeholder="WhatsApp (ex: 5598984533013)" required />
                      <input type="email" id="email" placeholder="E-mail (opcional)" style="grid-column:1 / -1" />
                    </div>

                    <div class="buttons">
                      <button type="button" class="btn ghost" id="btnBack">Voltar</button>
                      <button type="submit" class="btn success" id="btnSend">Receber minha análise</button>
                    </div>
                  </form>
                </div>

                <!-- Step 6 - Obrigado -->
                <div class="step" data-step="6" style="display:none;text-align:center;padding:18px">
                  <h2 class="question" id="thanksTitle">Obrigado!</h2>
                  <p class="hint" id="thanksSub">Recebemos seu diagnóstico. O Daniel analisará seus dados e entrará em contato pelo WhatsApp.</p>
                  <div style="margin-top:12px">
                    <a href="#" id="downloadGuide">Baixar guia: 5 erros ao financiar seu projeto (PDF)</a>
                  </div>
                </div>

              </div>
            </div>

            <!-- navigation -->
            <div style="margin-top:8px;display:flex;justify-content:space-between;align-items:center">
              <div class="small" id="skipHint">Preencha e receba uma análise personalizada.</div>
              <div>
                <button class="btn ghost" id="prevBtn" style="display:none">Voltar</button>
                <button class="btn primary" id="nextBtn">Próximo</button>
              </div>
            </div>
          </div>
        </div>

        <footer class="page-footer small">© <span id="yr"></span> ROD LIDER — Todos os direitos reservados</footer>
      </div>

      <!-- Sidebar -->
      <aside>
        <div class="card aside-block">
          <h3 style="margin:0 0 6px">Como funciona</h3>
          <div class="small">Responda 5 rápidas perguntas. Receba uma análise e um plano inicial por WhatsApp — sem compromisso.</div>
        </div>

        <div class="card aside-block">
          <h3 style="margin:0 0 6px">Clientes contemplados</h3>
          <div class="small">Na versão final, inclua galeria de fotos e depoimentos filtráveis por tipo de investimento.</div>
        </div>

        <div class="card aside-block">
          <h3 style="margin:0 0 6px">Fale agora</h3>
          <a class="cta-whats" href="https://wa.me/5598984533013" target="_blank" rel="noopener" style="display:inline-block;text-decoration:none">Chamar no WhatsApp</a>
          <div class="small" style="margin-top:8px">Telefone: (98) 9845-33013</div>
        </div>
      </aside>
    </div>
  </div>

  <script>
    // Estado
    const state = {
      step: 1,
      objetivo: '',
      sub: '',
      valor: 50000,
      parcela: 1000,
      nome: '',
      whatsapp: '',
      email: ''
    };

    const maxStep = 6;
    const nextBtn = document.getElementById('nextBtn');
    const prevBtn = document.getElementById('prevBtn');
    const progressText = document.getElementById('progressText');
    const stepArea = document.getElementById('stepArea');
    const choicesStep1 = document.getElementById('choicesStep1');
    const choicesStep2 = document.getElementById('choicesStep2');
    const valorRange = document.getElementById('valorRange');
    const valorText = document.getElementById('valorText');
    const parcelaRange = document.getElementById('parcelaRange');
    const parcelaText = document.getElementById('parcelaText');
    const btnBack = document.getElementById('btnBack');
    const btnSend = document.getElementById('btnSend');
    const leadForm = document.getElementById('leadForm');
    const yr = document.getElementById('yr');
    yr.innerText = new Date().getFullYear();

    // opções de subobjetivos
    const subs = {
      negocio: ["Marketing e Vendas","Compra de Equipamentos","Aumento de Estoque","Contratação de Equipe"],
      imovel: ["Morar","Alugar para terceiros","Reformar/Construir"],
      veiculo: ["Carro de passeio","Utilitário/Trabalho","Moto/Quadriciclo"],
      rural: ["Compra de gado","Compra de máquinas","Compra de terra"],
      outro: ["Descrição breve do projeto"]
    };

    // inicializar escolhas step1
    choicesStep1.querySelectorAll('.choice').forEach(c => {
      c.addEventListener('click', () => {
        choicesStep1.querySelectorAll('.choice').forEach(x=>x.classList.remove('active'));
        c.classList.add('active');
        state.objetivo = c.dataset.value;
        goStep(2);
      });
    });

    function populateStep2(){
      choicesStep2.innerHTML = '';
      const arr = subs[state.objetivo] || subs['outro'];
      arr.forEach(s => {
        const d = document.createElement('div');
        d.className = 'choice';
        d.textContent = s;
        d.addEventListener('click', () => {
          choicesStep2.querySelectorAll('.choice').forEach(x=>x.classList.remove('active'));
          d.classList.add('active');
          state.sub = s;
          goStep(3);
        });
        choicesStep2.appendChild(d);
      });
    }

    function updateProgress(){
      const visibleStep = state.step <=5 ? state.step : 6;
      progressText.innerText = state.step <=5 ? `Passo ${state.step} de 5` : `Finalizado`;
      document.querySelectorAll('.step').forEach(el => {
        el.style.display = el.dataset.step == state.step ? '' : 'none';
      });
      prevBtn.style.display = state.step > 1 && state.step <=5 ? '' : 'none';
      nextBtn.style.display = state.step < 5 ? '' : 'none';
      btnBack && (btnBack.style.display = state.step > 1 && state.step <=5 ? '' : 'none');
    }

    function goStep(n){
      state.step = n;
      if(n === 2) populateStep2();
      updateProgress();
    }

    nextBtn.addEventListener('click', () => {
      if(state.step === 1 && !state.objetivo) return;
      if(state.step === 2 && !state.sub) return;
      if(state.step >=5) return;
      goStep(state.step + 1);
    });
    prevBtn.addEventListener('click', () => {
      if(state.step <=1) return;
      goStep(state.step - 1);
    });
    btnBack && btnBack.addEventListener('click', () => {
      if(state.step <=1) return;
      goStep(state.step - 1);
    });

    // ranges
    valorRange.addEventListener('input', (e) => {
      state.valor = Number(e.target.value);
      valorText.innerText = formatBR(state.valor);
    });
    parcelaRange.addEventListener('input', (e) => {
      state.parcela = Number(e.target.value);
      parcelaText.innerText = formatBR(state.parcela);
    });

    // helper
    function formatBR(n){
      return 'R$ ' + Number(n).toLocaleString('pt-BR');
    }

    // envio do lead
    leadForm.addEventListener('submit', async (e) => {
      e.preventDefault();
      state.nome = document.getElementById('nome').value.trim();
      state.whatsapp = document.getElementById('whats').value.trim();
      state.email = document.getElementById('email').value.trim();
      if(!state.nome || !state.whatsapp){
        alert('Preencha seu nome e WhatsApp para prosseguir.');
        return;
      }

      // preparar payload
      const payload = {
        objetivo: state.objetivo,
        sub: state.sub,
        valor: state.valor,
        parcela: state.parcela,
        nome: state.nome,
        whatsapp: state.whatsapp,
        email: state.email,
        source: 'site-diagnostico'
      };

      // Tente enviar para endpoint /api/leads — substitua pela sua URL real
      try{
        await fetch('/api/leads', {
          method: 'POST',
          headers: {'Content-Type':'application/json'},
          body: JSON.stringify(payload)
        });
      }catch(err){
        console.warn('Envio falhou (placeholder):', err);
      }

      // enviar também mensagem rápida para WhatsApp (abre chat com mensagem pronta)
      const waNumber = state.whatsapp.startsWith('55') ? state.whatsapp : ('55' + state.whatsapp.replace(/\D/g,''));
      const msg = encodeURIComponent(`Olá, sou ${state.nome}. Fiz o diagnóstico no site: objetivo=${state.objetivo}, valor=${formatBR(state.valor)}, parcela=${formatBR(state.parcela)}. Aguardo contato.`);
      const waUrl = `https://wa.me/${waNumber}?text=${msg}`;
      // avança pro obrigado
      goStep(6);
      // abre whatsapp em nova aba depois de 1s
      setTimeout(()=> window.open(waUrl, '_blank'), 1000);
    });

    // botão enviar (quando alguém clicar no botão verde do form)
    btnSend.addEventListener('click', () => leadForm.dispatchEvent(new Event('submit', {cancelable: true})));

    // download do guia - placeholder
    const downloadGuide = document.getElementById('downloadGuide');
    downloadGuide.addEventListener('click', (e) => {
      e.preventDefault();
      // Substitua o href para o PDF real no servidor: /docs/guia-financiamento.pdf
      window.location.href = '/docs/guia-5-erros-financiamento.pdf';
    });

    // set initial values UI
    valorText.innerText = formatBR(state.valor);
    parcelaText.innerText = formatBR(state.parcela);
    updateProgress();
  </script>
</body>
</html>
