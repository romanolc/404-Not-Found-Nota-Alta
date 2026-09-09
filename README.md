# Implantação de Sistemas — Deployment Control Center v3

Plataforma acadêmica interativa para apresentar as três atividades práticas da disciplina **Implantação de Sistemas** com uma experiência visual inspirada em consoles de Deployment, DevOps, Cloud e SRE. A versão atual preserva a identidade visual premium da entrega anterior e adiciona uma abertura cinematográfica de apresentação.

## Splash screen de entrada

Antes do painel principal, o projeto exibe a abertura **404 Not Found: Nota Alta**, associada ao grupo e à atividade. A sequência tem boot de terminal com efeito de digitação, mensagens de sistema detectado, transformação visual de `404 / NOT FOUND` em `NOTA ALTA`, identificação da turma e do professor, fluxo luminoso `DEV → STAGING → PROD` e estado `DEPLOYMENT READY`. Em seguida, a camada converge e realiza uma transição com fade, blur e escala para revelar o site principal.

A intro dura aproximadamente 6,5 segundos, possui botão **PULAR INTRO**, aceita a tecla **ESC**, não reproduz áudio automaticamente, usa partículas leves em canvas e reduz efeitos quando `prefers-reduced-motion` está ativo ou quando a tela é pequena.

## Identificação

| Campo | Informação |
|---|---|
| Disciplina | Implantação de Sistemas |
| Turma | Desenvolvimento de Sistemas - 96213 |
| Professor | Celso Barreto |
| Data | 08/09/2026 |

### Equipe

- Brhayan Dias Ramos
- Ícaro Ricardo Rodrigues Santos
- João Guiherme Moreira
- Lucca Romano

## Atividades apresentadas

### Atividade 1 — Planejamento da implantação

Apresenta o contexto e as restrições do estudo de caso, o fluxo DEV → Integração/Testes → STAGING → PROD, arquitetura de servidores e componentes laterais, preparação de servidores, matriz de responsabilidades, calendário D-7 até D+7, agenda operacional da janela de quatro horas e Release Gate.

### Atividade 2 — Pipeline de implantação

Apresenta o pipeline COMMIT → BUILD → TESTES → ANÁLISE → ARTEFATO → STAGING → APROVAÇÃO → PRODUÇÃO, diferenciando automação e aprovação humana. Também inclui gestão de secrets, migrations, reconciliação, smoke tests executáveis e terminal/pipeline simulado.

### Atividade 3 — Incident Response

Apresenta a inconsistência entre o banco legado, com 12.540 pedidos, e o banco novo, com 12.317 pedidos. A diferença de 223 registros é investigada com uma sequência de oito passos, terminal simulado, evidências e decisão correta **NO-GO**, pois o sistema ainda não foi liberado aos usuários. O rollback é apresentado como sequência de recuperação e trilha de auditoria.

## Interações e animações

- Splash screen cinematográfica com boot, typing effect, partículas, grid, glitch sutil, glow, deployment flow e transição data-wipe.
- Botão Pular Intro e tecla ESC.
- Navegação SPA com scroll suave e seção ativa.
- Menu responsivo para celular.
- Modais acessíveis para ambientes, componentes e eventos da janela.
- Cards de investigação e preparação com feedback.
- Contadores animados do dashboard.
- Pipeline CI/CD com execução progressiva, estados e logs.
- Smoke tests executáveis com progresso e resultado.
- Checklist Go/No-Go com simulação de decisão.
- Simulação completa de deployment: preparação, backup, deploy, migration, validação, Go/No-Go e resultado bloqueado.
- Timeline, terminal simulado, toasts, hover states, foco visível e botão voltar ao topo.
- Animações discretas de fluxo, alerta pulsante, glow e entrada em viewport.
- `prefers-reduced-motion` respeitado para reduzir movimentos não essenciais.

## Tecnologias

- HTML5 semântico
- CSS3 com layout responsivo, glassmorphism, grids e animações
- JavaScript Vanilla
- Canvas leve para partículas da intro
- Google Fonts via CDN: Inter, Space Grotesk e JetBrains Mono

Não são utilizados React, Vue, Angular, TypeScript, Bootstrap, backend ou dependências de build. O projeto continua funcionando ao abrir diretamente o `index.html`.

## Estrutura

```text
implantacao-sistemas/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── assets/
└── README.md
```

## Execução local

Abra `index.html` diretamente no navegador. Para executar por um servidor local opcional:

```bash
cd implantacao-sistemas
python3 -m http.server 8000
```

Depois, acesse `http://localhost:8000`.

## Publicação no GitHub Pages

1. Crie um repositório no GitHub.
2. Faça upload dos arquivos mantendo a estrutura de pastas.
3. Faça commit e push para a branch principal.
4. Abra **Settings → Pages**.
5. Selecione **Deploy from a branch**, escolha a branch principal e a pasta `/root`.
6. Salve e aguarde a URL pública do GitHub Pages.

## Base acadêmica

O conteúdo segue o material fornecido pelo professor: implantação como transição controlada; ambientes; servidores; preparação de infraestrutura; estratégias; backup e recuperação; RPO/RTO; migrations; migração e reconciliação; rollback; automação; CI/CD; containers; IaC; segurança; secrets; testes; observabilidade; indicadores; documentação; riscos; checklist; Go/No-Go e o estudo de caso da inconsistência de pedidos.

Os indicadores de monitoramento, as execuções e a animação da intro são simulações front-end para fins acadêmicos. Nenhum dado real é acessado ou alterado.

## Sistema de áudio

A interface inclui o card futurista **AUDIO SYSTEM** no Hero, com a faixa `Not Found` do artista `Not Found`. O arquivo está em `assets/music/not-found.mp3`. O player utiliza `<audio>` HTML5 com controles personalizados para play/pause, progresso com seek, duração, volume, estado de reprodução, equalizador animado, ondas de áudio e feedback visual. O áudio não inicia automaticamente: a reprodução depende da ação do usuário.

## Melhoria de Rollback e validação pré-Go-Live

A seção de Rollback também explicita que rollback é uma medida de recuperação, não uma substituição dos testes. O fluxo normal apresentado é **Implementação → Testes → Validação → Evidências → Go/No-Go → Produção**. Em caso de falha crítica, o fluxo alternativo é **Falha → NO-GO → Preservar evidências → Rollback → Testar novamente → Validar → Estado estável**.

Foram incluídos painéis de testes técnicos, testes de dados, smoke tests, testes funcionais e validação de negócio. O incidente da Atividade 3 aparece conectado ao processo de reconciliação: banco legado com 12.540 pedidos, banco novo com 12.317, diferença de 223 pedidos (aproximadamente 1,78%), evidência que conduz ao NO-GO antes da liberação aos usuários.
