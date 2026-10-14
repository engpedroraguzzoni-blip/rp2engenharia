# RP2 Engenharia — Plano Técnico Incremental P2

**Versão:** 1.1 — especificação técnica com registro da P2.1 aprovada  
**Data:** 14/10/2026  
**Status:** planejamento das waves futuras; P2.1 implementada, verificada e aprovada em 14/10/2026 (estado operacional no runbook)  
**Repositório:** `engpedroraguzzoni-blip/rp2engenharia`  
**Branch de trabalho:** `feat/cabanas-steel-frame`  
**Aplicação:** `cabanas/` — Astro + TypeScript + Tailwind CSS 4  
**Primeira entrega visual:** P2.1 — aprovada em 14/10/2026; próxima wave prevista: P2.2, ainda sem autorização de execução

> **Finalidade deste documento:** estabelecer a arquitetura e os critérios técnicos do site de Cabanas Modulares da RP2 Engenharia e registrar as decisões de implementação já aprovadas da P2.1. As waves seguintes continuam sendo planejamento. O runbook operacional define ordem de execução, status, checklists e checkpoints; este plano define a solução técnica. Não há instruções para implementar todas as seções de uma só vez.

## 1. Objetivo e produto

Construir uma experiência comercial da **RP2 Engenharia — Cabanas Modulares**, com apresentação institucional na abertura, identidade própria da RP2 e navegação progressiva para conhecer os modelos e solicitar informações.

O site está previsto para **três modelos de cabanas**. Neste momento, somente a **Cabana Siena** possui informações técnicas e comerciais disponibilizadas. Os outros dois modelos serão definidos posteriormente; não inventar nomes, preços, dimensões, imagens, descrições ou disponibilidade.

A **Hero apresenta a RP2 e sua linha de cabanas**; não é uma Hero de produto e não deve se concentrar na Siena. A Siena será apresentada em seção própria da Home e, se houver necessidade futura, em página de detalhe.

### Decisões de produto

- Site de Cabanas desenvolvido dentro de `cabanas/`, separado do HTML institucional existente.
- Home institucional/comercial, orientada à apresentação da marca, aos modelos e à conversão.
- Abertura com vídeo de fundo fornecido pelo responsável. As capturas Nature Haus e a captura `hero-rp2.png` orientaram composição; a identidade aplicada é a RP2.
- Menu superior **flutuante e persistente durante a rolagem**, com aparência adaptada à posição da página.
- Construção e aprovação **uma seção por vez**.
- Dados comerciais baseados exclusivamente em materiais aprovados; não preencher modelos faltantes com conteúdo fictício.
- Publicação, URL definitiva e ligação com o site institucional pertencem à fase posterior de implantação.

## 2. Base técnica e limites

A preparação P1 estabeleceu a aplicação independente em `cabanas/`, com **Astro estático, TypeScript estrito e Tailwind CSS 4**, sem necessidade prevista de React, SSR, CMS ou backend para esta fase. O estado final da P1 foi informado no runbook existente; conferir apenas a estrutura efetivamente presente antes de editar código.

**Não executar na P2 sem nova autorização:** modificar o HTML institucional, `main`, DNS, Vercel, domínio, rewrites, redirects, deploy, merge, PR ou publicação; instalar dependências por conveniência; criar catálogo com dados fictícios, checkout, simulador ou formulário sem destino de dados definido.

### Fontes de referência e responsabilidade

| Fonte | Responsabilidade |
|---|---|
| `docs/RP2_DESIGN_SYSTEM.md` | Identidade, fontes, tokens, componentes, espaçamentos e diretrizes de marca |
| `docs/RP2_CABANA_SIENA_FICHA_TECNICA_COMERCIAL.md` | Dados técnicos, modalidades e preços da Siena |
| `docs/RP2_CABANAS_RUNBOOK_OPERACIONAL.md` | Ordem operacional, gates, aprovações e registro de execução |
| `docs/RP2_P1_PLANO_TECNICO.md` | Arquitetura e decisões técnicas da preparação P1 |
| `docs/RP2_P2_PLANO_VISUAL_FUNCIONAL.md` | Referência histórica/conceitual, sem segunda fila de execução |
| Sites Nature Haus e Atualle; capturas `hero-01.png`, `menu-flutuante.png` e `hero-rp2.png` fornecidas pelo responsável | Referência de composição e comportamento. Não publicar capturas ou ativos das marcas de referência. |

**Hierarquia:** dados de produto vêm das respectivas fichas aprovadas; identidade vem do Design System; este plano define a arquitetura; o runbook coordena a execução. Caso haja conflito, registrar a dúvida e não improvisar.

O Design System e a ficha Siena deverão ser lidos em seus arquivos originais antes de codificar. Até essa leitura, cores e informações reproduzidas de documentos anteriores devem ser tratadas como referências, não como autorização para substituir o conteúdo canônico.

## 3. Organização técnica da aplicação

Estrutura conceitual, a ser adaptada à árvore real sem recriar arquivos existentes:

```text
rp2engenharia/
├── <site-institucional-existente>.html  # preservar exatamente como está
├── docs/
│   ├── RP2_DESIGN_SYSTEM.md
│   ├── RP2_CABANA_SIENA_FICHA_TECNICA_COMERCIAL.md
│   ├── RP2_P2_PLANO_TECNICO_INCREMENTAL.md
│   └── RP2_CABANAS_RUNBOOK_OPERACIONAL.md
└── cabanas/
    ├── public/
    │   ├── videos/
    │   │   └── <video-hero-aprovado>.mp4
    │   └── images/
    │       ├── branding/
    │       │   └── <logomarca-rp2>
    │       ├── hero/
    │       │   └── <poster-hero-aprovado>  # se disponível/aprovado
    │       └── modelos/
    └── src/
        ├── components/
        │   ├── Hero.astro               # nome sugerido
        │   └── SiteHeader.astro         # separar somente se útil
        ├── data/
        │   └── cabanas.ts               # quando houver dados estruturados
        ├── layouts/
        │   └── BaseLayout.astro
        ├── pages/
        │   └── index.astro
        └── styles/
            └── global.css
```

**Regra de caminhos:** assets servidos pelo Astro ficam em `cabanas/public/`, não presumidamente em `public/` na raiz. Na P2.1, os nomes reais confirmados são `hero.mp4`, `logo RP2.png` e `hero-poster.png`; novos arquivos devem ser conferidos sem mover ou converter originais automaticamente. O caminho público resulta em `/videos/<arquivo>` ou `/images/branding/<arquivo>` na aplicação.

### Responsabilidades de implementação

- `BaseLayout.astro`: base HTML, idioma `pt-BR`, metas locais iniciais e CSS global.
- `index.astro`: composição progressiva das seções efetivamente construídas.
- `Hero.astro`: mídia, overlay, conteúdo de abertura e CTAs da Hero.
- `SiteHeader.astro`: logomarca, navegação, ação comercial e comportamento persistente ao rolar; deve ser reutilizável depois da Hero.
- Componentes auxiliares de vídeo ou cards: criar **somente se a implementação concreta justificar**.
- `src/data/`: manter dados de modelos e preços em fonte única quando passarem a ser utilizados. Não inserir dois registros fictícios para completar três posições.

Priorizar HTML semântico, componentes `.astro` e CSS/Tailwind. JavaScript no cliente apenas para comportamento que CSS/HTML nativos não resolvam adequadamente, sobretudo estado visual do header e navegação mobile.

## 4. Direção visual da Home

A Home deve proporcionar uma entrada cinematográfica, com linguagem sofisticada, clara e comercial. Os sites Nature Haus e Atualle orientam comportamento/composição; a captura `hero-rp2.png` registra a direção visual proposta para RP2. Não reproduzir marcas, textos, cores, fotografias ou código das referências.

**Composição de referência observada:** vídeo/imagem paisagística ocupando a tela; logomarca no topo esquerdo; navegação central; CTA à direita; título expressivo e botões à esquerda; possíveis informações flutuantes à direita; sinal visual de continuidade para baixo. Ao rolar, a referência mantém um menu em barra sólida no topo.

**Identidade RP2:** aplicar integralmente a versão canônica do Design System. Como ponto de partida registrado no runbook existente: Barlow Condensed para títulos/ações, Barlow para corpo; vermelho `#C0251F`, hover `#A01D18`, texto `#1A1818`, off-white `#F4F2F0` e branco `#FFFFFF`. Validar os tokens no documento antes da implementação. **Não adotar a paleta verde/dourada da referência**.

A orientação visual deve se manter coerente em desktop, tablet e mobile, preservando a leitura do vídeo e o protagonismo da marca.

## 5. P2.1 — Especificação técnica da Hero institucional

### 5.1 Papel e limites

A Hero apresenta a **RP2 Engenharia e sua linha de Cabanas Modulares**. Não mostrar metragens, preços ou nome da Siena como mensagem principal. Nenhum modelo específico deve dominar a abertura.

**Entregas da P2.1:** Hero em vídeo, overlay de legibilidade, logomarca RP2, cabeçalho flutuante persistente, texto institucional, CTAs com destinos reais, composição responsiva, acessibilidade e testes locais.

**Não incluir:** cards com atributos não comprovados, seção de modelos, preços, galeria, FAQ, rodapé definitivo ou páginas de detalhe. O header funcional pertence a esta primeira wave; futuras waves refinam sua navegação sem reconstruí-lo.

### 5.2 Fundo em vídeo

- Usar o vídeo aprovado `cabanas/public/videos/hero.mp4` como fundo decorativo. Arquivo confirmado: MP4, 1280 × 720, 8 s, aproximadamente 6,6 MB.
- Elemento `<video>` decorativo com `autoplay`, `muted`, `loop` e `playsinline`; sem controles expostos na Hero se for apenas fundo.
- Dimensionar com `object-fit: cover` e posição de enquadramento ajustável por breakpoint, de forma a preservar o motivo visual relevante.
- Aplicar sobreposição preta com base de 60% e gradientes laterais/inferiores; a área de texto recebe escurecimento adicional para manter contraste. A referência detalhada de contraste está no checkpoint P2.1 do runbook.
- Usar `cabanas/public/images/hero/hero-poster.png` durante o carregamento, na falha de reprodução e quando movimento reduzido for solicitado. O poster deriva de `cabanas/Hero-1.png`, cujo original foi preservado.
- Com `prefers-reduced-motion: reduce`, manter o poster, não atribuir fonte ao vídeo e não iniciar reprodução. O conteúdo aparece sem animação.
- No mobile, evitar carregamento pesado desnecessário quando a mídia não puder ser exibida adequadamente; validar em dispositivo real quando possível.
- Considerar MP4 H.264 como escolha preferencial de compatibilidade; medir tamanho/duração e propor otimização **sem modificar o original sem aprovação**.
- Não presumir que um vídeo gerado por IA represente uma obra real entregue pela RP2. Não acompanhar a mídia com legendas que façam essa alegação.

### 5.3 Header superior flutuante e persistente

O comportamento faz parte da **P2.1**, não fica adiado até o fechamento da página.

1. **Na abertura:** header sobreposto à Hero, com logo à esquerda, identificação “Cabanas Modulares” ao centro e CTA de WhatsApp à direita. A identificação central não é um link.
2. **Durante a rolagem:** header permanece fixo no topo e adota fundo claro translúcido, texto escuro e sombra/borda discretas, sem deslocar o conteúdo.
3. **Sem saltos de layout:** reservar espaços necessários, evitar deslocamento de conteúdo, configurar `z-index` coerente e áreas clicáveis confortáveis.
4. **Links válidos:** inserir apenas âncoras de seções já implementadas, rotas reais ou canais oficiais confirmados. Não usar `href="#"` como simulação, nem publicar itens clicáveis para seções inexistentes.
5. **Mobile na P2.1:** marca e CTA permanecem disponíveis; a identificação central é ocultada. Não há menu expansível enquanto os destinos de navegação não existirem.
6. **Comportamento progressivo:** se for necessário detectar scroll, usar mecanismo leve (por exemplo, `IntersectionObserver` ou listener otimizado), sem biblioteca adicional. Garantir aparência legível também quando JavaScript não estiver disponível.
7. **Futuro:** novas âncoras serão adicionadas conforme seções aprovadas. O header será refinado, não refeito.

O aspecto de barra sólida ao rolar será **inspirado na captura da referência**, mas com as cores, fontes e logomarca RP2.

### 5.4 Conteúdo editorial e hierarquia

**Hierarquia pretendida:** pequeno identificador da linha de cabanas → título institucional de impacto → subtítulo breve → uma ou duas ações úteis → indicação de continuidade para a próxima seção, quando existir.

Texto aprovado pelo responsável para a P2.1:

- Identificador: **RP2 Engenharia · Cabanas Modulares**
- Título: **Arquitetura para viver mais perto da natureza.**
- Apoio: **Conheça a linha de cabanas modulares em Steel Frame da RP2 Engenharia.**

Não atribuir a todas as cabanas características ainda não verificadas: personalização integral, execução em determinado prazo, isolamento quantificado, número de quartos, garantia, economia percentual ou preço uniforme.

**CTAs implementados na P2.1:** “Conversar sobre cabanas” na Hero e “Falar com a RP2” no header abrem o WhatsApp aprovado `+55 24 99284-8489`, com mensagem sobre as cabanas. Não há link para modelos/seções ainda inexistentes.

### 5.5 Cards informativos flutuantes

A referência apresenta cards no lado direito; para a RP2, serão **opcionais**, sujeitos a aprovação visual e conteúdo comprovado. Não reproduzir frases da marca de referência como “100% personalizável”, “execução rápida” ou “design atemporal” como fatos da RP2 sem documentação.

Os cards não podem competir com o título nem comprometer a composição no mobile. Se não houver fatos institucionais adequados e aprovados, omitir cards na primeira versão em vez de preencher com generalidades não verificadas.

### 5.6 Responsividade

| Faixa de revisão | Comportamento esperado |
|---|---|
| Desktop (~1440 px e acima) | Vídeo amplo; logo, navegação e CTA distribuídos; título à esquerda e área visual do vídeo valorizada |
| Tablet (~768 px) | Redução proporcional de tipografia/espaçamentos; header compacto; possíveis cards reposicionados ou ocultados |
| Mobile (~390 px e abaixo) | Conteúdo essencial em uma coluna; headline legível; botões sem colisões; vídeo bem enquadrado; menu utilizável por toque |

Preferir medidas fluidas, `min-height` adequada à viewport e atenção a navegadores móveis com barras dinâmicas (`svh`/`dvh` quando apropriado). Considerar áreas seguras (`safe-area-inset-*`) e não causar overflow horizontal. Imagens/vídeo não devem bloquear a leitura dos CTAs.

### 5.7 Acessibilidade, semântica e desempenho

- Apenas um título principal (`h1`) na Home, localizado na Hero.
- Usar marca com texto alternativo adequado; imagem decorativa de vídeo não necessita descrição redundante, mas precisa de fallback visual.
- Assegurar contraste real sobre o vídeo em todos os frames relevantes, estados de foco visíveis e navegação por teclado.
- Respeitar redução de movimento. A abertura CSS da Hero e do conteúdo interno do header conclui em aproximadamente 920 ms, sem depender do vídeo; com movimento reduzido, o conteúdo aparece diretamente. O header revela o contêiner se ele receber foco durante a abertura.
- Garantir que vídeo e imagens não causem deslocamentos de layout; testar poster e falha de reprodução.
- Carregar fontes de forma coerente com o projeto existente; não duplicar downloads desnecessários.
- Avaliar o peso do vídeo, carregamento inicial, experiência com conexão limitada e comportamento mobile antes de publicar.

### 5.8 Gate técnico da P2.1

A entrega P2.1 foi aprovada pelo responsável em 14/10/2026. O aceite e as evidências constam no runbook. Os critérios técnicos que sustentaram esse gate foram:

- Hero institucional com vídeo e logo reais, fundo/fallback coerentes e header persistente funcionando no scroll.
- Conteúdo sem características inventadas nem foco indevido em apenas um modelo.
- Todos os botões renderizados funcionando e levando a destinos existentes.
- Desktop/tablet/mobile verificados, sem cortes críticos, scroll horizontal ou perda de legibilidade.
- `npm run check` e `npm run build` aprovados **dentro de `cabanas/`**; `git diff --check` e `git status --short` revisados.
- HTML institucional intacto; nenhum commit, push ou deploy automático.
- Responsável aprova o resultado antes de iniciar P2.2.

### 5.9 Registro da implementação aprovada

A P2.1 foi conferida pelo responsável no navegador e aprovada em 14/10/2026. Os detalhes do aceite, gates, evidências e limites de validação constam no checkpoint P2.1 do `docs/RP2_CABANAS_RUNBOOK_OPERACIONAL.md`. Este plano registra as decisões técnicas para evitar que propostas antigas sejam confundidas com o que está implementado.

- **Vídeo e poster:** `public/videos/hero.mp4` e `public/images/hero/hero-poster.png`; logo em `public/images/branding/logo RP2.png`.
- **Texto:** identificador, título e apoio aprovados conforme seção 5.4; o apoio menciona Steel Frame.
- **Overlay:** preto, base 60%, com gradientes de contraste para o conteúdo.
- **Contato:** CTA da Hero e do header para o WhatsApp institucional aprovado; sem âncoras de seções futuras.
- **Movimento:** abertura CSS em sequência, cerca de 920 ms; redução de movimento mantém conteúdo visível e poster estático.
- **Comportamento do vídeo:** carregar/reproduzir sem depender da animação da Hero; em falha ou redução de movimento, manter poster.

## 6. Dados e expansão para três modelos

Planejar uma fonte única de dados, criada apenas quando a primeira seção de modelos ou preços precisar dela, capaz de representar informações opcionais e um **estado editorial** (`rascunho`/`publicável`, ou equivalente). Apenas dados de modelos aprovados podem ser expostos na Home.

Um contrato conceitual possível:

```ts
type Cabana = {
  slug: string;
  nome: string;
  publicavel: boolean;
  areaM2?: number;
  sistemaConstrutivo?: string;
  imagemPrincipal?: string;
  modalidadeKit?: { precoInicialBRL: number };
  modalidadePronta?: { precoInicialBRL: number };
};
```

**Atenção:** o contrato é ilustrativo, não obrigação de implementar agora. Não criar objetos `modelo-2`/`modelo-3` fictícios nem cards “em breve” sem decisão editorial. A Siena pode ser o único registro publicado até as fichas restantes serem aprovadas. Não pressupor que preços, modalidades ou especificações da Siena se aplicam aos demais modelos.

### Informação disponível para Siena

- **Nome:** Cabana Siena.
- **Área:** 26 m².
- **Sistema:** Steel Frame.
- **Kit para montagem:** a partir de **R$ 59.970,00**.
- **Composição da cabana pronta:** a partir de **R$ 164.000,00**, incluindo o kit no valor total.

Esses preços devem ser mostrados **somente junto da modalidade correta e das ressalvas comerciais aprovadas**. Frete, gestão de obra e demais exclusões devem ser verificados na ficha; não anunciar o valor da modalidade pronta como empreitada fixa ou “chave na mão”. Valores não entram na Hero institucional por padrão.

## 7. Arquitetura incremental das demais seções

As próximas waves são direções técnicas e **não autorizam implementação**. A ordem operacional definitiva e os checkpoints constarão do runbook atualizado após a aprovação deste plano.

| Wave | Seção / responsabilidade técnica |
|---|---|
| **P2.1** | Hero institucional, vídeo, overlay, logo, header flutuante e ações válidas |
| **P2.2** | Apresentação da RP2 no segmento de cabanas; proposta de valor com texto aprovado |
| **P2.3** | Área de modelos, orientada a dados; somente modelos com conteúdo autorizado |
| **P2.4** | Apresentação detalhada da Cabana Siena e galeria de imagens reais aprovadas |
| **P2.5** | Modalidades de contratação efetivamente disponíveis para cada modelo, começando pela Siena |
| **P2.6** | Preços iniciais, ressalvas e condições comerciais, próximos aos modelos correspondentes |
| **P2.7** | Informações técnicas e materiais documentados, sem generalização indevida entre cabanas |
| **P2.8** | FAQ baseado em condições oficiais e dúvidas comerciais confirmadas |
| **P2.9** | Contato/CTA final, rodapé e acabamento da navegação responsiva já iniciada na Hero |
| **P2.10** | Revisão integrada de visual, navegação, acessibilidade, responsividade e build local |

Não criar antecipadamente seções vazias, rotas de modelos sem dados ou links quebrados. Se as outras duas fichas ainda não estiverem disponíveis quando a seção de modelos for construída, deixar explícita a dependência e publicar apenas informação aprovada.

## 8. Processo de construção incremental

A execução de cada wave seguirá este ciclo:

1. Ler este plano técnico, o trecho relevante do Design System, as fichas aplicáveis e o runbook operacional.
2. Confirmar branch, estado do Git e arquivos já existentes; preservar alterações e assets do responsável.
3. Implementar **somente a seção autorizada** e a infraestrutura mínima indispensável.
4. Revisar a seção visualmente com o responsável e iterar na própria wave até aprovação.
5. Verificar em desktop, tablet e mobile; executar gates proporcionais à alteração.
6. Registrar checkpoint curto no runbook; somente então avançar.

A P2.1 foi refinada nas rodadas **A — estrutura/vídeo/header**, **B — composição/copy**, **C — mobile/performance/acessibilidade** e **D — aceite/checkpoint**. Essas divisões registram o fluxo concluído e não são motivo para reconstruir componentes prontos.

## 9. Restrições de publicação e preservação

- Manter o HTML institucional inalterado durante toda a P2.
- Não mudar configuração da Vercel, URL base, DNS ou roteamento até a fase de publicação.
- Não publicar capturas, código, logos, textos ou mídias da Nature Haus como ativos RP2.
- Não usar imagens genéricas para representar cabanas da RP2, nem atribuir a vídeos conceituais o status de registro de obra real.
- Não renomear, sobrescrever ou otimizar arquivos originais sem autorização; gerar derivados quando aprovados.
- Não realizar commit/push/deploy por padrão; solicitar autorização específica.

## 10. Pendências a resolver no momento certo

| Item | Quando resolver | Regra até lá |
|---|---|---|
| Vídeo da Hero | Resolvido na P2.1 | `cabanas/public/videos/hero.mp4` |
| Logomarca RP2 | Resolvido na P2.1 | `cabanas/public/images/branding/logo RP2.png` |
| Poster/fallback do vídeo | Resolvido na P2.1 | `cabanas/public/images/hero/hero-poster.png`; original preservado |
| Copy da Hero | Aprovada na P2.1 | Texto final consta na seção 5.4 |
| Canal geral do CTA sobre cabanas | Aprovado na P2.1 | WhatsApp institucional `+55 24 99284-8489`; fluxo de orçamento por produto/modalidade ainda será definido |
| Links de “modelos” no menu/CTAs | Quando a seção P2.3 existir | Não criar âncoras mortas |
| Nomes, fichas e fotografias das outras duas cabanas | Antes de publicá-las em P2.3 | Não criar modelos falsos |
| Política comercial aplicável a cada novo modelo | Ao receber as respectivas fichas | Não copiar preços ou condições da Siena |
| Endereço público e integração com institucional | Fase de publicação | Não antecipar configurações Vercel |

## 11. Critérios de aceite do plano técnico

- [ ] A Hero está especificada como apresentação **institucional** da RP2 Cabanas, sem foco em modelo isolado.
- [ ] O vídeo, a logomarca e a referência visual possuem funções técnicas claramente definidas.
- [ ] O menu superior flutuante e persistente está incluído na P2.1.
- [ ] A Home está preparada conceitualmente para **três modelos** sem dados inventados.
- [ ] A Siena mantém suas informações e condições próprias, fora da Hero institucional.
- [ ] O plano preserva Design System, aplicação Astro, HTML institucional e limites de P1.
- [ ] As waves seguintes estão descritas de forma incremental e sem duplicar o runbook.
- [ ] Pendências reais estão explícitas; nenhuma foi preenchida por suposição.

**Estado:** a implementação e o aceite da P2.1 estão registrados no runbook. A próxima wave prevista é P2.2; seu conteúdo deverá ser planejado e autorizado antes da implementação. As demais waves permanecem pendentes.


## 12. Histórico documental

| Versão | Data | Alteração |
|---|---|---|
| 1.0 | 14/10/2026 | Especificação técnica inicial das waves da P2. |
| 1.1 | 14/10/2026 | Registro do aceite P2.1 e atualização de copy, mídia, contato, overlay, header e movimento conforme implementação. |
