<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rafael Schultzweiter - Painel Musical Interativo</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        gold: { 400: '#f3c649', 500: '#d4af37', 600: '#aa820a' },
                        dark: { 900: '#0a0a0c', 800: '#121216', 700: '#1c1c24' }
                    },
                    fontFamily: {
                        heading: ['Cinzel', 'serif'],
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; background-color: #0a0a0c; color: #e5e7eb; }
        h1, h2, h3, h4, .font-heading { font-family: 'Cinzel', serif; }
        .gold-gradient-text { background: linear-gradient(135deg, #fff2a3 0%, #d4af37 50%, #aa820a 100%); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 350px; max-height: 400px; }
        .glass-panel { background: rgba(28, 28, 36, 0.6); backdrop-filter: blur(12px); border: 1px solid rgba(212, 175, 55, 0.15); }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #0a0a0c; }
        ::-webkit-scrollbar-thumb { background: #d4af37; border-radius: 4px; }
    </style>
</head>
<body class="antialiased overflow-x-hidden relative">

    <!-- Chosen Palette: Dark Gold & Warm Neutrals (Black, Gold, Warm Gray) -->
    <!-- Application Structure Plan: The SPA is structured as an interactive artist dashboard. It transforms the textual portfolio into a data-driven experience. Sections include: 'Visão Geral' (executive summary), 'Análise de Repertório' (quantitative chart analysis of 800+ songs), 'Arsenal Técnico' (qualitative breakdown of skills), and 'Material de Performance' (media evidence). This structure was chosen to allow event organizers to quickly assess the musician's versatility, quantitative repertoire size, and qualitative performance through interactive exploration rather than reading a static bio. -->
    <!-- Visualization & Content Choices: 1. Repertoire by Genre (Donut Chart) -> Goal: Show versatility -> Viz: Chart.js Donut -> Interaction: Hover for exact song counts -> Justification: Best for part-to-whole relationships. 2. Era Distribution (Bar Chart) -> Goal: Highlight decades covered -> Viz: Chart.js Bar -> Interaction: Hover tooltips -> Justification: Excellent for comparing chronological distributions. 3. Multi-instrumentalist Grid -> Goal: Detail technical capacity -> Viz: CSS/Tailwind Grid with Unicode -> Interaction: Hover effects -> Justification: Clean, scannable categorization. NO SVG/Mermaid used. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <nav class="fixed top-0 w-full z-50 glass-panel border-b-0 px-6 py-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <div class="font-heading font-bold text-xl text-white tracking-widest">
                <span class="text-gold-500">&#x1F3B8;</span> R. SCHULTZWEITER
            </div>
            <div class="hidden md:flex space-x-6 text-sm font-semibold">
                <a href="#overview" class="hover:text-gold-400 transition">Visão Geral</a>
                <a href="#dados" class="hover:text-gold-400 transition">Análise de Dados</a>
                <a href="#tecnica" class="hover:text-gold-400 transition">Arsenal Técnico</a>
                <a href="#midia" class="hover:text-gold-400 transition">Performance</a>
            </div>
            <a href="#contato" class="bg-gold-500 text-dark-900 px-4 py-2 rounded-lg font-bold text-sm hover:bg-gold-400 transition">&#x1F4F2; Contratar</a>
        </div>
    </nav>

    <main class="pt-24 pb-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto space-y-24">

        <section id="overview" class="grid lg:grid-cols-2 gap-12 items-center min-h-[70vh]">
            <div class="space-y-6">
                <div class="inline-block px-3 py-1 rounded-full border border-gold-500/30 text-gold-400 text-xs font-bold uppercase tracking-widest bg-gold-500/10">
                    Relatório Artístico Executivo
                </div>
                <h1 class="text-4xl md:text-5xl lg:text-6xl font-heading font-bold leading-tight">
                    Música que Marca <br><span class="gold-gradient-text">Momentos e Faz Lembranças</span>
                </h1>
                <p class="text-gray-400 text-lg leading-relaxed">
                    Esta aplicação apresenta a síntese profissional de Rafael Schultzweiter. Um músico autodidata focado na entrega autêntica de voz, violão e instrumentação múltipla. Explore abaixo a análise quantitativa e qualitativa de um portfólio desenvolvido para elevar o padrão de eventos, festas e confraternizações.
                </p>
                <div class="glass-panel p-6 rounded-2xl border-l-4 border-l-gold-500">
                    <p class="italic text-gray-300">"Sem a música, a vida seria um erro, uma tarefa cansativa e um exílio."</p>
                    <p class="text-gold-400 text-sm font-bold mt-2">— Friedrich Nietzsche</p>
                </div>
            </div>
            <div class="relative">
                <div class="absolute inset-0 bg-gold-500/20 blur-3xl rounded-full"></div>
                <img src="WhatsApp Image 2026-08-30 at 13.09.38 (1).jpeg" alt="Rafael Schultzweiter" class="relative rounded-2xl border border-gold-500/30 shadow-2xl w-full object-cover max-h-[600px]">
            </div>
        </section>

        <section id="dados" class="space-y-12">
            <div class="text-center max-w-3xl mx-auto">
                <h2 class="text-3xl font-heading font-bold mb-4">Análise Quantitativa do Repertório</h2>
                <p class="text-gray-400">
                    O painel a seguir desmembra o acervo musical de mais de 800 canções ativas. Os gráficos interativos demonstram a versatilidade necessária para adaptação a diferentes perfis de público e naturezas de eventos. Interaja com as legendas e barras para explorar os dados granulares.
                </p>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <div class="glass-panel p-6 rounded-3xl">
                    <h3 class="text-xl font-bold mb-2 text-white">Distribuição por Gênero Musical</h3>
                    <p class="text-sm text-gray-400 mb-6 border-b border-gray-700 pb-4">Proporção estimada de estilos musicais dominantes no setlist, evidenciando foco em Rock, MPB e Pop.</p>
                    <div class="chart-container">
                        <canvas id="genreChart"></canvas>
                    </div>
                </div>

                <div class="glass-panel p-6 rounded-3xl">
                    <h3 class="text-xl font-bold mb-2 text-white">Cobertura Cronológica (Décadas)</h3>
                    <p class="text-sm text-gray-400 mb-6 border-b border-gray-700 pb-4">Volume de canções por época, destacando a especialização em 'Flashbacks' e clássicos radiofônicos.</p>
                    <div class="chart-container">
                        <canvas id="decadeChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="tecnica" class="space-y-12">
            <div class="text-center max-w-3xl mx-auto">
                <h2 class="text-3xl font-heading font-bold mb-4">Arsenal Técnico e Instrumental</h2>
                <p class="text-gray-400">
                    A estrutura de uma apresentação solo exige dinâmica. Abaixo estão catalogados os instrumentos dominados de forma autodidata, garantindo riqueza sonora através de arranjos que combinam cordas, sopro, teclas e percussão adaptada (pandeirola de pé).
                </p>
            </div>

            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4" id="instrumentGrid">
            </div>
            <p class="text-center text-sm text-gold-400 font-bold mt-4">Nota do Artista: "Só não tenho bateria ainda &#x1F605;"</p>
        </section>

        <section id="midia" class="space-y-12">
             <div class="text-center max-w-3xl mx-auto">
                <h2 class="text-3xl font-heading font-bold mb-4">Evidência de Performance</h2>
                <p class="text-gray-400">
                    Registros audiovisuais de atuações cruas e reais. A observação direta do método de execução valida a proposta de valor: música ao vivo autêntica, sem artifícios, construída sobre técnica vocal pura e acompanhamento instrumental simultâneo.
                </p>
            </div>

            <div class="grid lg:grid-cols-12 gap-8">
                <div class="lg:col-span-7 glass-panel p-4 rounded-3xl">
                    <div class="relative w-full rounded-2xl overflow-hidden bg-black aspect-video flex items-center justify-center border border-gray-700">
                        <video controls poster="WhatsApp Image 2026-08-30 at 13.09.38.jpeg" class="w-full h-full object-cover">
                            <source src="1000758566.mp4" type="video/mp4">
                            Navegador não suporta vídeo.
                        </video>
                    </div>
                    <div class="mt-4 px-2 flex justify-between items-center text-sm">
                        <span class="text-gold-400 font-bold">&#x1F534; Gravação Ao Vivo (Raw)</span>
                        <span class="text-gray-400">Voz, Violão & Pandeirola</span>
                    </div>
                </div>

                <div class="lg:col-span-5 grid grid-cols-2 gap-4">
                    <div class="rounded-2xl overflow-hidden border border-gray-700 hover:border-gold-500 transition-colors">
                        <img src="WhatsApp Image 2026-08-30 at 12.40.33 (1).jpeg" alt="Show" class="w-full h-full object-cover">
                    </div>
                    <div class="rounded-2xl overflow-hidden border border-gray-700 hover:border-gold-500 transition-colors">
                        <img src="WhatsApp Image 2026-08-30 at 13.09.38.jpeg" alt="Palco" class="w-full h-full object-cover">
                    </div>
                    <div class="rounded-2xl overflow-hidden border border-gray-700 hover:border-gold-500 transition-colors">
                        <img src="WhatsApp Image 2026-08-30 at 12.40.33.jpeg" alt="Evento" class="w-full h-full object-cover">
                    </div>
                    <div class="rounded-2xl overflow-hidden border border-gray-700 hover:border-gold-500 transition-colors">
                        <img src="WhatsApp Image 2026-08-30 at 13.09.39.jpeg" alt="Ambiente" class="w-full h-full object-cover">
                    </div>
                </div>
            </div>
        </section>

        <section id="contato" class="glass-panel p-8 md:p-12 rounded-3xl border border-gold-500/40 mt-12 relative overflow-hidden">
            <div class="absolute -right-20 -top-20 w-64 h-64 bg-gold-500/10 rounded-full blur-3xl"></div>
            
            <div class="grid md:grid-cols-2 gap-12 relative z-10">
                <div>
                    <h2 class="text-3xl font-heading font-bold mb-4">Módulo de Contratação</h2>
                    <p class="text-gray-400 mb-8">
                        Utilize a interface ao lado para processar os parâmetros do seu evento. O sistema compilará as informações e iniciará um protocolo de comunicação direta via WhatsApp com o artista para agendamento e viabilidade.
                    </p>
                    
                    <div class="space-y-4">
                        <div class="flex items-center gap-4 text-white">
                            <span class="text-2xl text-gold-500">&#x1F4DE;</span>
                            <div>
                                <div class="text-xs text-gray-400 uppercase tracking-widest">Linha Direta</div>
                                <div class="font-bold text-xl">(21) 97695-2645</div>
                            </div>
                        </div>
                        <div class="flex items-center gap-4 text-white">
                            <span class="text-2xl text-gold-500">&#x1F4C5;</span>
                            <div>
                                <div class="text-xs text-gray-400 uppercase tracking-widest">Disponibilidade</div>
                                <div class="font-bold text-lg">Eventos, Festas, Bares</div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-dark-900 p-6 rounded-2xl border border-gray-700">
                    <form id="contactForm" class="space-y-4">
                        <div>
                            <label class="block text-xs font-bold text-gray-400 mb-1">Nome do Solicitante</label>
                            <input type="text" id="inpName" required class="w-full bg-dark-800 border border-gray-700 rounded-lg p-3 text-white focus:outline-none focus:border-gold-500 transition">
                        </div>
                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-bold text-gray-400 mb-1">Tipo de Evento</label>
                                <select id="inpEvent" class="w-full bg-dark-800 border border-gray-700 rounded-lg p-3 text-white focus:outline-none focus:border-gold-500 transition">
                                    <option>Festa Particular</option>
                                    <option>Bar/Restaurante</option>
                                    <option>Confraternização</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-xs font-bold text-gray-400 mb-1">Data/Local</label>
                                <input type="text" id="inpDate" placeholder="Ex: 10/12 - Centro" class="w-full bg-dark-800 border border-gray-700 rounded-lg p-3 text-white focus:outline-none focus:border-gold-500 transition">
                            </div>
                        </div>
                        <button type="submit" class="w-full bg-gold-500 text-dark-900 font-bold text-lg py-4 rounded-lg hover:bg-gold-400 transition mt-4">
                            &#x1F4E2; Gerar Requisição no WhatsApp
                        </button>
                    </form>
                </div>
            </div>
        </section>

    </main>

    <footer class="text-center py-8 text-gray-600 text-sm border-t border-gray-800 mt-12">
        <p>&#x1F3B8; Rafael Schultzweiter Data Dashboard &copy; 2026. Todos os direitos reservados.</p>
    </footer>

    <script>
        const appState = {
            genres: ['Rock', 'MPB', 'Pop (Nac/Int)', 'Blues & Soul', 'Country/Sertanejo', 'Outros (Flashbacks)'],
            genreData: [210, 180, 150, 90, 100, 70],
            decades: ['Anos 60', 'Anos 70', 'Anos 80', 'Anos 90', 'Anos 2000'],
            decadeData: [90, 160, 250, 180, 120],
            instruments: [
                { name: 'Violão', icon: '&#x1F3B8;' },
                { name: 'Guitarra', icon: '&#x1F3B8;' },
                { name: 'Gaita', icon: '&#x1F3B9;' },
                { name: 'Teclado', icon: '&#x1F3B9;' },
                { name: 'Cavaquinho', icon: '&#x1F3BB;' },
                { name: 'Contra Baixo', icon: '&#x1F3B8;' },
                { name: 'Ukulele', icon: '&#x1F3B8;' },
                { name: 'Pandeirola (Pé)', icon: '&#x1F941;' },
                { name: 'Kazoo', icon: '&#x1F3BA;' }
            ]
        };

        Chart.defaults.color = '#9ca3af';
        Chart.defaults.font.family = "'Plus Jakarta Sans', sans-serif";

        const ctxGenre = document.getElementById('genreChart').getContext('2d');
        new Chart(ctxGenre, {
            type: 'doughnut',
            data: {
                labels: appState.genres,
                datasets: [{
                    data: appState.genreData,
                    backgroundColor: ['#d4af37', '#aa820a', '#f3c649', '#6b7280', '#4b5563', '#374151'],
                    borderColor: '#0a0a0c',
                    borderWidth: 2
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'right' },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return ' ' + context.raw + ' Músicas estimadas';
                            }
                        }
                    }
                }
            }
        });

        const ctxDecade = document.getElementById('decadeChart').getContext('2d');
        new Chart(ctxDecade, {
            type: 'bar',
            data: {
                labels: appState.decades,
                datasets: [{
                    label: 'Volume de Músicas',
                    data: appState.decadeData,
                    backgroundColor: '#d4af37',
                    borderRadius: 6
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    y: { beginAtZero: true, grid: { color: '#1c1c24' } },
                    x: { grid: { display: false } }
                },
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        callbacks: {
                            title: function(context) {
                                let label = context[0].label || '';
                                if (label.length > 16) {
                                    return label.substring(0, 16) + '...';
                                }
                                return label;
                            }
                        }
                    }
                }
            }
        });

        const grid = document.getElementById('instrumentGrid');
        appState.instruments.forEach(inst => {
            const div = document.createElement('div');
            div.className = 'glass-panel p-4 rounded-xl text-center hover:bg-gold-500/10 hover:border-gold-500/50 transition cursor-default group';
            div.innerHTML = '<div class="text-3xl mb-2 group-hover:scale-110 transition-transform">' + inst.icon + '</div><div class="text-sm font-bold text-gray-300">' + inst.name + '</div>';
            grid.appendChild(div);
        });

        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const n = document.getElementById('inpName').value;
            const ev = document.getElementById('inpEvent').value;
            const d = document.getElementById('inpDate').value || 'A definir';
            const txt = 'Ol%C3%A1%20Rafael!%20Vim%20pelo%20Painel%20Interativo.%0A%0A*Nome:*%20' + encodeURIComponent(n) + '%0A*Evento:*%20' + encodeURIComponent(ev) + '%0A*Data/Local:*%20' + encodeURIComponent(d);
            window.open('https://wa.me/5521976952645?text=' + txt, '_blank');
        });
    </script>
</body>
</html>
```
