# RP2 Engenharia — Design System

**Versão:** 1.1 — inventário institucional e aplicação aprovada na página Cabanas  
**Data da análise do HTML institucional:** 13/10/2026  
**Atualização da aplicação Cabanas:** 14/10/2026  
**Status:** inventário do HTML institucional e guia visual; o adendo Cabanas registra a aplicação P2.1 sem representar refatoração do HTML institucional  
**Projeto:** RP2 Engenharia e Empreendimentos  
**Repositório de destino:** `engpedroraguzzoni-blip/rp2engenharia`  
**Branch de trabalho prevista:** `feat/cabanas-steel-frame`  
**Local sugerido no repositório:** `docs/RP2_DESIGN_SYSTEM.md`

> **Fonte da verdade:** HTML fornecido para análise (`RP2_Engenharia_Site(1).html`, idêntico ao arquivo de texto anexado). Os valores marcados **[EXISTENTE]** foram extraídos desse arquivo, incluindo o `<style>` e os atributos `style`. As diretrizes **[RECOMENDADO]** são propostas para futuras implementações — não devem ser confundidas com algo já implementado. Nenhuma mudança no código-fonte é pressuposta por este documento.

## 0. Como usar este documento no Codex

1. Antes de modificar o site, localizar o arquivo HTML real **no repositório local** e confirmar sua estrutura e branch. O nome do arquivo anexado **não comprova** qual é o nome do arquivo versionado.
2. Considerar os tokens e componentes **[EXISTENTE]** como base visual. Reutilizar os seletores quando apropriado, sem copiar indiscriminadamente estilos de contexto.
3. Para uma nova página, conservar a identidade (cores, tipografia, espaçamentos e padrões de interação), mas criar classes específicas quando necessário; não replicar grandes blocos de `style` inline sem motivo.
4. Tratar **[RECOMENDADO]** e **[PENDENTE]** como orientações ou decisões futuras, nunca como comportamentos garantidos do site atual.
5. Trabalhar na branch `feat/cabanas-steel-frame`, não alterar `main`, não fazer commit/push sem autorização do responsável pela tarefa.
6. Este documento orienta **aparência e comportamento**; não constitui aprovação de textos comerciais, percentuais, preços, imagens ou informações da empresa.

### Escopo

- Inclui: identidade, cores, fontes, hierarquia de texto, grids, espaçamentos, componentes, imagens, animações, responsividade e critérios para adicionar páginas.
- Não inclui: redesign, implementação de menu mobile, criação da página Cabanas ou alterações no HTML original.
- Não presume ferramentas como React, Tailwind, Bootstrap ou pipeline de build: o arquivo analisado é HTML + CSS + JavaScript puro.

---

## 1. Arquitetura e convenções existentes

**[EXISTENTE]** O projeto recebido reúne conteúdo em um documento HTML com:

- `<style>` interno no `<head>` e estilos adicionais em vários atributos `style` (199 elementos com `style` na versão analisada).
- JavaScript em `<script>` ao final do `<body>`; há também um bloco `application/ld+json` para dados estruturados.
- Fontes externas carregadas do Google Fonts.
- Imagens em *data URI* (`data:image/...;base64,...`) no HTML e em declarações CSS. Foram identificados **25 elementos `<img>` com data URI**, além de imagens de fundo incorporadas em CSS.
- Âncoras internas (`#sobre`, `#portfolio` etc.) como padrão dos links da navegação.
- Classes e IDs em português e inglês; manter os nomes existentes até que uma refatoração tenha escopo aprovado.

**[RECOMENDADO]** Em alterações pontuais, fazer o menor diff possível. Não introduzir bundlers, bibliotecas, novas famílias tipográficas ou renomeações em massa apenas para criar uma página interna.

---

## 2. Cores e tokens

### 2.1 Variáveis canônicas do CSS

**[EXISTENTE]** Todos os 13 tokens abaixo estão declarados no `:root`. Os identificadores e valores devem ser preservados literalmente.

| Token CSS | Valor exato | Uso observado / orientação |
|---|---|---|
| `--white` | `#FFFFFF` | Fundos e texto sobre vermelho/escuro |
| `--off-white` | `#F4F2F0` | Fundos alternados, painéis e cards |
| `--light` | `#E8E5E2` | Superfícies claras, trilhas e chips |
| `--mid` | `#C8C4C0` | Cinza intermediário disponível; utilização pontual |
| `--text` | `#1A1818` | Texto principal e seções escuras |
| `--text2` | `#5A5654` | Texto secundário e descrições |
| `--text3` | `#8A8482` | Legendas, placeholders e metadados |
| `--red` | `#C0251F` | Cor institucional, botões, detalhes e destaques |
| `--red2` | `#A01D18` | Hover de botões, variação escura do vermelho |
| `--red3` | `#E03530` | Acento mais claro em superfícies escuras |
| `--red-light` | `#F5EAEA` | Fundo suave de destaques, avisos e tags |
| `--border` | `#E0DCDA` | Bordas neutras e separadores |
| `--border2` | `rgba(192,37,31,0.2)` | Contorno vermelho translúcido |

```css
/* [EXISTENTE] Copiado dos tokens do arquivo-fonte */
:root {
  --white: #FFFFFF;
  --off-white: #F4F2F0;
  --light: #E8E5E2;
  --mid: #C8C4C0;
  --text: #1A1818;
  --text2: #5A5654;
  --text3: #8A8482;
  --red: #C0251F;
  --red2: #A01D18;
  --red3: #E03530;
  --red-light: #F5EAEA;
  --border: #E0DCDA;
  --border2: rgba(192,37,31,0.2);
}
```

### 2.2 Cores e efeitos fora do `:root`

**[EXISTENTE]** O site usa também valores literais ou semitransparentes:

| Valor | Contexto de uso |
|---|---|
| `#25D366` | Fundo do botão flutuante WhatsApp (`#wpp-float`) |
| `#242020` | Hover de `.diff-card` |
| `#9A9694` | Texto de `.diff-card p` |
| `rgba(255,255,255,.96)` | Fundo translúcido do menu fixo |
| `rgba(0,0,0,.08)` | Sombra do menu após rolagem |
| `rgba(240,238,236,.82)` | Sobreposição da imagem do Hero |
| `rgba(255,255,255,.12)` e `rgba(255,255,255,.25)` | Fundo/borda dos badges do Hero |
| `rgba(255,255,255,.7)`, `.65`, `.55`, `.45`, `.35`, `.2`, `.08`, `.025` | Textos, linhas e detalhes em seções escuras/vermelhas, em contextos distintos |
| `rgba(192,37,31,.6)` | Camada vermelha sobre uma imagem da seção Processo |
| `#1a3a1a`, `#7ec87e`, `#2d5a2d` | Badge verde específico de “Chalés · Steel Frame” |
| `#1a3a2a`, `#2d5a40`, `#2a1a0a`, `#5a3a10` | Valores auxiliares presentes em estilos inline de badges/cards de projetos |

> Atenção: as cores de apoio acima **não são novos tokens institucionais**. Alguns valores aparecem uma única vez e podem fazer parte de um contexto específico.

### 2.3 Semântica visual

**[RECOMENDADO]** Para novas páginas:

- **CTA primário e destaque:** `var(--red)`; hover `var(--red2)`.
- **Texto principal:** `var(--text)`; descritivo: `var(--text2)`.
- **Seções claras:** alternar `var(--white)` e `var(--off-white)` de acordo com a composição.
- **Seções escuras:** `var(--text)` como fundo e `var(--white)` para títulos, com `var(--red3)` para ênfase.
- **Divisórias:** `var(--border)` ou os separadores já existentes.
- **Cores especiais:** WhatsApp e badges temáticos apenas em seu contexto.
- Evitar inventar novos vermelhos/cinzas sem justificativa visual explícita.

**[PENDENTE]** A acessibilidade/contraste de todas as combinações não foi auditada em navegador. Cor por si só não deve transmitir informação essencial.

---

## 3. Tipografia

### 3.1 Fontes e carregamento

**[EXISTENTE]**

```html
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@300;400;500;600;700;800&family=Barlow:wght@300;400;500;600&display=swap" rel="stylesheet">
```

| Família | Pesos solicitados no carregamento | Uso |
|---|---|---|
| `'Barlow', sans-serif` | 300, 400, 500, 600 | Texto corrido, formulário e descrições; padrão do `<body>` |
| `'Barlow Condensed', sans-serif` | 300, 400, 500, 600, 700, 800 | Títulos, menu, botões, labels, métricas e badges |

A configuração global do corpo é:

```css
/* [EXISTENTE] */
body {
  background: var(--white);
  color: var(--text);
  font-family: 'Barlow', sans-serif;
  font-weight: 400;
  line-height: 1.6;
  overflow-x: hidden;
}
```

O `html` utiliza `scroll-behavior: smooth`. O CSS global também aplica `box-sizing: border-box` e `margin: 0; padding: 0` a todos os elementos/pseudoelementos.

### 3.2 Escala e hierarquia efetivamente usadas

**[EXISTENTE]** Não há uma escala tipográfica unificada em variáveis (`--font-*`); os tamanhos estão distribuídos pelas classes e por estilos inline.

| Papel / seletor | `font-size` | Peso | `line-height` | Detalhes |
|---|---|---|---|---|
| Hero `.hero-title` | `clamp(3.8rem,6.5vw,6.5rem)` | 800 | `.95` | Condensed, uppercase, `letter-spacing:-.02em` |
| Título de seção `.section-title` | `clamp(2.2rem,4vw,3.5rem)` | 800 | `1` | Condensed, uppercase, `letter-spacing:-.01em` |
| Eyebrow `.eyebrow` | `.68rem` | 600 | herdado | Condensed, uppercase, `letter-spacing:.35em` |
| Tag Hero `.hero-tag` | `.7rem` | 600 | herdado | Condensed, uppercase, `letter-spacing:.3em` |
| Subtexto Hero `.hero-sub` | `1.05rem` | 400 herdado | `1.8` | largura máxima `46ch` |
| Texto “Sobre” `.sobre-text p` | `.95rem` | 400 herdado | `1.9` | cor `--text2` |
| Link menu `.nav-links a` | `.78rem` | 500 | herdado | Condensed, uppercase, `letter-spacing:.1em` |
| CTA topo `.nav-cta` | `.78rem` | 700 | herdado | Condensed, uppercase, `letter-spacing:.15em` |
| Botão `.btn-red` e `.btn-outline-dark` | `.82rem` | 700 | herdado | Condensed, uppercase, `letter-spacing:.2em` |
| Estatísticas `.hero-stat-num` | `2.6rem` | 800 | `1` | Condensed, vermelho |
| Estatísticas `.hero-stat-label` | `.7rem` | herdado | herdado | uppercase, `letter-spacing:.1em` |
| Diferenciais `.diff-card h3` | `1.15rem` | 700 | herdado | Condensed, uppercase, `letter-spacing:.05em` |
| Diferenciais `.diff-card p` | `.85rem` | 400 herdado | `1.7` | cor literal `#9A9694` |
| Benefício Steel Frame `.sf-benefit h4` | `1.05rem` | 700 | herdado | Condensed, uppercase |
| Nome de projeto `.proj-name` | `1.6rem` | 800 | `1` | Condensed, uppercase; destacado: `2.2rem` |
| Tipo de projeto `.proj-type` | `.72rem` | 500 | herdado | Condensed, uppercase |
| Descrição de projeto `.proj-desc` | `.84rem` | 400 herdado | `1.7` | cor `--text2` |
| Badge `.proj-badge` | `.6rem` | 700 | herdado | Condensed, uppercase, `letter-spacing:.25em` |
| Formulário `.form-label` | `.65rem` | 600 | herdado | Condensed, uppercase |
| Formulário `.form-input` | `.9rem` | 400 herdado | herdado | Barlow |
| Formulário `.form-submit` | `.85rem` | 700 | herdado | Condensed, uppercase |
| Rodapé `.footer-copy` | `.72rem` | herdado | herdado | `letter-spacing:.04em` |

**Importante:** “herdado” significa que a classe não declara aquele atributo explicitamente; o valor final pode depender do elemento ancestral ou das regras do navegador. `rem` é relativo à fonte raiz do navegador (não existe redefinição explícita de `font-size` em `html` neste HTML).

### 3.3 Regras tipográficas para conteúdo novo

**[RECOMENDADO]**

- H1 visual de destaque: reaproveitar a linguagem de `.hero-title`, com uma única tag semântica `<h1>` por página.
- H2 de seção: `.section-title` e uso pontual de `<span>` vermelho.
- Sobretítulo: `.eyebrow`; preservar traço vermelho via `::before`.
- Descrições: fonte Barlow, cor `--text2`, entre `.84rem` e `1.05rem` conforme o componente existente mais próximo.
- CTA/badge: Barlow Condensed, peso 600/700, maiúsculas e espaçamento entre letras já adotado.
- Não transformar os valores acima em uma nova escala abstrata sem aprovação; a prioridade é a consistência visual com o site recebido.

---

## 4. Layout e espaçamentos

### 4.1 Base de layout

**[EXISTENTE]**

```css
section { padding: 6rem 5rem; }
nav { padding: 1.2rem 5rem; }
#hero { min-height: 100vh; padding: 8rem 5rem 5rem; }
```

Não há `max-width` global para o conteúdo de todas as seções. O alinhamento horizontal parte predominantemente de `5rem` de padding lateral no desktop.

| Área / seletor | Comportamento existente |
|---|---|
| `nav` | Flex, `justify-content:space-between`, posição fixa, `z-index:100` |
| `.nav-links` | Flex, `gap:2.5rem` |
| `.hero-content` | `max-width:56%` no desktop |
| `.hero-actions` | Flex, `gap:1rem`, quebra de linha habilitada |
| `.hero-stats` | Flex, `gap:3rem` |
| `.sobre-grid` | Grid `1fr 1fr`, `gap:6rem` |
| `.sf-grid` | Grid `1fr 1fr`, `gap:5rem` |
| `.contato-grid` | Grid `1fr 1.2fr`, `gap:5rem` |
| `.diff-grid` | Grid `repeat(3,1fr)`, `gap:1px` |
| `.portfolio-grid` | Grid `repeat(3,1fr)`, `gap:1.5rem` |
| `.proj-card.featured` | Ocupa 2 colunas do grid; conteúdo interno em `1fr 1fr` |
| `.steps-grid` | Grid `repeat(4,1fr)` |
| `.depo-grid` | Grid `1fr 1fr` no CSS; no HTML há override inline `repeat(auto-fit,minmax(280px,1fr))` |
| `.form-grid` | Grid `1fr 1fr`, `gap:1rem` |
| `#blog-grid` | Grid inline `1.4fr 1fr 1fr`, `gap:1.5rem` |
| `#galeria` | Seção com padding inline `4rem 5rem`; grade interna inline com 4 colunas e `gap:3px` |
| `footer` | Flex horizontal, `padding:2.5rem 5rem`, com quebra de linha |

### 4.2 Espaçamentos recorrentes

**[EXISTENTE]** O projeto não define tokens de spacing. Valores observados que podem orientar novas composições:

| Contexto | Valor |
|---|---|
| Espaço após eyebrow | `margin-bottom:1rem` |
| Espaço após `.section-title` | `margin-bottom:.8rem` |
| Régua de seção `.section-rule` | `width:48px`, `height:3px`, `margin:1.5rem 0 2rem` |
| Início de vários grids após título | `margin-top:3rem` |
| Espaço entre cards do portfólio | `1.5rem` |
| Padding de `.diff-card` | `2.5rem 2rem` |
| Padding de `.form-wrap` | `2.5rem` |
| Padding de `.depo-card` | `2.2rem` |
| Padding de `.sf-visual` | `2.5rem` |
| Padding de `.proj-card-header` | `1.8rem 1.8rem 1.4rem` |
| Padding de `.proj-card-body` | `0 1.8rem 1.8rem` |

**[RECOMENDADO]** Em novas seções, preferir esses valores já usados. Ajustes excepcionais devem ser locais e documentados, sem alterar indiscriminadamente os estilos compartilhados.

### 4.3 Bordas, cantos, formas e sombras

**[EXISTENTE]**

- Borda predominante: `1px solid var(--border)`.
- CTA e cards são majoritariamente **retangulares, sem `border-radius`**. Não introduzir cartões/pílulas muito arredondados como padrão.
- Exceções: o círculo das etapas de processo (`border-radius:50%`) e a barra de rolagem personalizada (`border-radius:2px`).
- Menu: fundo translúcido `rgba(255,255,255,.96)`, `backdrop-filter:blur(12px)` e `border-bottom:1px solid var(--border)`.
- Após rolagem (`nav.scrolled`): `box-shadow:0 2px 20px rgba(0,0,0,.08)`.
- Hero: recortes geométricos com `clip-path:polygon(...)`, usando vermelhos `--red` e `--red2`.

---

## 5. Biblioteca de componentes: contratos existentes

> Os exemplos de código nesta seção são **recortes de referência**, não um kit de componentes independente. Aplicam-se quando os estilos correspondentes do HTML original estão carregados.

### 5.1 Cabeçalho / navegação

**[EXISTENTE]** Seletores: `nav`, `nav.scrolled`, `.nav-logo`, `.nav-logo-mark`, `.nav-logo-text`, `.nav-links`, `.nav-cta`.

- Posição fixa no topo, ocupa a largura da tela, fundo branco semitransparente.
- Logo é tipográfico: `RP` + `2` em `<sub>`, seguido de “Engenharia”.
- Links do menu são uppercase, `.78rem`, peso 500, em Barlow Condensed, com hover vermelho.
- Botão direito `.nav-cta`: vermelho `--red`, padding `.55rem 1.6rem`, muda para `--red2` no hover.
- Itens atuais: **Sobre, Diferenciais, Steel Frame, Galeria, Blog, Portfólio, Contato**; CTA **Falar com a RP2**.
- `#mainnav` recebe a classe `scrolled` quando `window.scrollY > 40`.
- Os itens navegam por âncoras da própria página. A logo usa `href="#"`.

**[PENDENTE]** Em largura de até 960px, `.nav-links` usa `display:none`; não foi identificado menu hamburguer substituto. O CTA do menu permanece, sujeito ao espaço disponível.

**[RECOMENDADO]** Para a página de Cabanas, usar link relativo ao HTML correto, preservando o CTA. Verificar a versão mobile antes de considerar a navegação concluída.

### 5.2 Hero / abertura

**[EXISTENTE]** Seletores: `#hero`, `.hero-overlay`, `.hero-accent`, `.hero-accent-inner`, `.hero-content`, `.hero-tag`, `.hero-title`, `.hero-sub`, `.hero-actions`, `.hero-stats`, `.hero-badge`.

- Hero cobre ao menos `100vh`, tem imagem de fundo `center center / cover` e overlay claro.
- Faixas geométricas vermelhas ocupam `42%` da direita no desktop.
- Conteúdo textual ocupa até `56%` do contêiner.
- Título forte em caixa alta, com palavra destacada em `--red`.
- Ações são links estilizados com `.btn-red` e `.btn-outline-dark`.
- Painel lateral contém badges translúcidos sobre vermelho.
- Faixas laterais e badges da direita desaparecem em larguras ≤ 960px.

Exemplo de marcação do texto (adaptar conteúdo, sem copiar o Hero inteiro):

```html
<div class="hero-tag">Steel Frame · Alto Padrão</div>
<h1 class="hero-title">TÍTULO <span>EM DESTAQUE</span></h1>
<p class="hero-sub">Descrição breve do serviço ou empreendimento.</p>
<div class="hero-actions">
  <a class="btn-red" href="#contato">Solicitar proposta</a>
  <a class="btn-outline-dark" href="#detalhes">Conhecer detalhes</a>
</div>
```

**Nota:** o HTML acima é **[RECOMENDADO] exemplo de uso das classes**, não um trecho literal completo da página atual. As âncoras `#contato` e `#detalhes` só devem ser usadas se os respectivos IDs existirem na página de destino.

### 5.3 Cabeçalho de seção

**[EXISTENTE]** `.eyebrow`, `.section-title`, `.section-title span`, `.section-rule`.

```html
<!-- [RECOMENDADO] Padrão montado com classes existentes -->
<div class="eyebrow">Nosso diferencial</div>
<h2 class="section-title">CONSTRUÇÃO COM <span>PRECISÃO</span></h2>
<div class="section-rule"></div>
```

- Eyebrow: traço vermelho via `::before`, largura `20px`, altura `2px`.
- Título: peso 800, Condensed, uppercase, escala fluida.
- Régua decorativa: `48px × 3px`.
- Em seção escura, o código atual aplica overrides por contexto (`#diferenciais .section-title`, por exemplo); não assumir que o mesmo componente muda automaticamente de cor em qualquer fundo escuro.

### 5.4 Botões e ações

| Classe | Aparência | Padding | Hover |
|---|---|---|---|
| `.btn-red` | Fundo `--red`, texto branco | `.8rem 2.2rem` | `--red2`, deslocamento vertical `-2px` |
| `.btn-outline-dark` | Borda `2px solid --text`, texto escuro | `.8rem 2.2rem` | Borda e texto `--red` |
| `.nav-cta` | Fundo vermelho, texto branco | `.55rem 1.6rem` | Fundo `--red2` |
| `.wpp-cta` | Botão retangular vermelho com ícone WhatsApp | `1rem 1.8rem` | Fundo `--red2` |
| `.form-submit` | Fundo `--text`, texto branco, largura `100%` | `.85rem 2rem` | Fundo `--red` |

**[RECOMENDADO]** Usar `<a>` para navegação e `<button>` para ações de formulário. Não substituir contraste/bordas sem teste.

### 5.5 Cards e destaques

**[EXISTENTE]**

| Família | Seletores | Contrato visual |
|---|---|---|
| Equipe | `.team-card`, `.team-avatar`, `.team-name`, `.team-role` | Card claro com borda, linha vermelha na esquerda e tipografia condensada |
| Indicadores | `.sobre-highlights`, `.highlight-box`, `.highlight-num` | Painéis brancos separados por `1px`, números vermelhos grandes |
| Diferenciais | `.diff-grid`, `.diff-card`, `.diff-num`, `.diff-line` | Cards escuros; hover muda fundo para `#242020` |
| Benefícios LSF | `.sf-benefit`, `.sf-benefit-num` | Linhas horizontais com numeração grande em vermelho translúcido |
| Portfólio | `.proj-card`, `.proj-card.featured`, `.proj-name`, `.proj-desc` | Borda clara, fundo off-white, hover sobe `4px` e destaca borda vermelha |
| Chips de características | `.proj-specs`, `.proj-spec` | Fundo `--light`, texto `--text2`, caixa alta, `.65rem` |
| Status de projeto | `.proj-badge` + modificadores | Tags pequenas, condensadas, uppercase |
| Processo | `.step-item`, `.step-circle` | Quatro etapas numeradas com círculos brancos/vermelhos sobre fundo vermelho |
| Depoimentos | `.depo-card`, `.depo-text`, `.depo-author` | Card branco com borda, citação em itálico e aspas decorativas |
| Contato | `.contato-item`, `.contato-icon`, `.contato-label` | Lista com ícones em fundo `--red-light` e divisórias |

**Modificadores de status implementados no CSS:**

| Classe | Fundo | Texto | Borda adicional |
|---|---|---|---|
| `.proj-badge.entregue` | `--text` | `--white` | Não |
| `.proj-badge.em-obra` | `--red` | `--white` | Não |
| `.proj-badge.fase-branca` | `--off-white` | `--text` | `1px solid --border` |
| `.proj-badge.lancamento` | `--red-light` | `--red` | `1px solid --border2` |

Outros badges do portfólio são construídos com atributos `style` e podem não seguir exatamente esses modificadores.

### 5.6 Barras e métricas

**[EXISTENTE]** `.sf-track` tem altura `4px` e cor `--light`; `.sf-fill` tem fundo `--red` e inicia com `width:0`, animando para o valor do atributo `data-w`. `.proj-bar-track` tem altura `3px`, `.proj-bar-fill` tem fundo vermelho.

A largura animada de barras LSF **não corresponde necessariamente** ao percentual escrito no rótulo; por exemplo, “Velocidade de Obra +40%” usa `data-w="88"`. Reaproveitar somente a apresentação, não a interpretação ou os dados sem validação.

### 5.7 Formulário

**[EXISTENTE]** `.form-wrap`, `.form-title`, `.form-grid`, `.form-group`, `.form-label`, `.form-input`, `.form-submit`.

```css
/* [EXISTENTE] Regras centrais */
.form-input {
  background: var(--white);
  border: 1px solid var(--border);
  color: var(--text);
  padding: .75rem 1rem;
  font-family: 'Barlow', sans-serif;
  font-size: .9rem;
  outline: none;
  transition: border-color .2s;
  resize: vertical;
}
.form-input:focus { border-color: var(--red); }
.form-input::placeholder { color: var(--text3); }
```

O formulário solicita nome, telefone, e-mail, tipo de projeto e mensagem. O botão executa `enviar()` que valida nome e telefone e abre um link do WhatsApp com texto preenchido. **Não foi identificado envio a backend.** O campo de e-mail está presente no HTML, mas não é incluído na mensagem construída pela função `enviar()`.

**[RECOMENDADO]** Preservar a aparência; revisar associação `label`/`for`, acessibilidade de foco, validação e comportamento mobile quando uma alteração de formulário fizer parte do escopo.

### 5.8 Rodapé e WhatsApp

**[EXISTENTE]** `footer`, `.footer-logo`, `.footer-copy`, `.footer-links` formam o rodapé escuro. O CTA flutuante `#wpp-float` é fixo, quadrado (`50px × 50px`), verde `#25D366`, no canto inferior direito (`bottom/right:2rem`), `z-index:200`.

**[RECOMENDADO]** Reutilizar em novas páginas somente após conferir destino dos links, número e texto da mensagem. Não assumir que âncoras da home funcionem em outra página.

---

## 6. Responsividade: comportamento real

### 6.1 Breakpoints declarados

**[EXISTENTE]** O CSS usa dois limites principais:

- `@media (max-width: 960px)` — reestruturação ampla de navegação e grids.
- `@media (max-width: 600px)` — `.diff-grid` e `.form-grid` viram uma coluna.

Há ainda um segundo bloco `@media (max-width:960px)` aplicado especificamente a `#blog` e `#blog-grid`.

### 6.2 Regras efetivamente aplicadas em ≤ 960px

| Seletor | Mudança |
|---|---|
| `nav` | `padding:1rem 2rem` |
| `.nav-links` | `display:none` |
| `section` | `padding:4rem 2rem` |
| `#hero` | `padding:6rem 2rem 4rem` |
| `.hero-content` | `max-width:100%` |
| `.hero-accent`, `.hero-accent-inner`, `.hero-right-content` | `display:none` |
| `.hero-stats` | `flex-wrap:wrap; gap:2rem` |
| `.sobre-grid`, `.sf-grid`, `.contato-grid` | `grid-template-columns:1fr; gap:2.5rem` |
| `.diff-grid` | 2 colunas |
| `.portfolio-grid` | 1 coluna |
| `.proj-card.featured` | deixa de ocupar 2 colunas e passa a uma coluna interna |
| `.steps-grid` | 2 colunas; linha conectora ocultada |
| `.depo-grid` | Regra de uma coluna no stylesheet; pode ser sobreposta pelo `style` inline do HTML |
| `footer` | Coluna, centralizado, `padding:2rem` |
| `.portfolio-header` | Coluna, alinhado à esquerda |
| `#blog-grid` | Uma coluna com `!important` |
| `#blog` | `padding:4rem 2rem!important` |

Em ≤ 600px, `.diff-grid` e `.form-grid` tornam-se uma coluna.

### 6.3 Riscos existentes — não são padrões desejáveis

**[PENDENTE]**

1. **Menu mobile:** os links somem em ≤ 960px e não há um menu alternativo definido no arquivo analisado. Incluir novo item apenas na lista desktop não garante acesso mobile.
2. **Galeria:** o grid interno está em `style="grid-template-columns:repeat(4,1fr)"` sem regra responsiva específica. O padding `4rem 5rem` do `#galeria` também é inline e pode prevalecer sobre `section{padding:4rem 2rem}`. Isso merece teste visual.
3. **Depoimentos:** o `style` inline com `repeat(auto-fit,minmax(280px,1fr))` pode prevalecer sobre a regra `.depo-grid{grid-template-columns:1fr}` do media query.
4. **Outros layouts inline:** mosaicos do portfólio e imagens têm dimensões fixas específicas; verificar cortes, altura e possíveis estouros antes de generalizá-los.
5. **`overflow-x:hidden` no body:** pode esconder overflow visual, mas não corrige um layout responsivo quebrado.

**[RECOMENDADO]** Testar ao menos larguras próximas a **1440px, 1024px, 960px, 768px, 600px, 390px e 320px**. Essas larguras são uma **grade de teste proposta**, não breakpoints adicionais do CSS.

---

## 7. Imagens, mídia e composição

**[EXISTENTE]**

- Há fundos e imagens com data URI Base64 no HTML. O arquivo anexado contém 25 tags `<img>`, cada uma com fonte Base64; pelo menos dois fundos CSS reutilizam um data URI no Hero e no card de equipe.
- As imagens de projeto e galeria frequentemente usam `object-fit:cover`, com `object-position` variável (`center`, `center top`, `center 25%`, etc.).
- A Galeria usa mosaico com imagens em alturas de `260px` e `127px`, gap de `3px` e hover com `transform:scale(1.04)` em `0.4s`.
- Fotos da equipe utilizam overlay em gradiente preto para legibilidade dos nomes.
- Há imagens com `loading="lazy"`; nem todas o possuem.
- O Hero tem sobreposição clara para priorizar legibilidade do texto sobre a foto.
- O rodapé e o WhatsApp usam elementos SVG/ícones no próprio HTML.

**[RECOMENDADO]**

- Priorizar imagens reais e autorizadas da RP2; não transformar imagens de referência em prova de obra entregue.
- Para novas imagens, escolher o corte usando `object-fit:cover` e `object-position` de acordo com a composição; nunca presumir que todos os cortes são iguais.
- Manter `alt` descritivo, dimensões coerentes e carregamento adequado; considerar arquivos de imagem externos em vez de grandes blocos Base64 apenas se a mudança arquitetural for aprovada.
- Não copiar imagens de outros projetos para a página Cabanas sem autorização de uso e pertinência ao projeto.

---

## 8. Movimento, interação e JavaScript

### 8.1 Reveal ao rolar

**[EXISTENTE]**

```css
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity .65s ease, transform .65s ease;
}
.reveal.visible { opacity: 1; transform: none; }
.reveal-left {
  opacity: 0;
  transform: translateX(-24px);
  transition: opacity .65s ease, transform .65s ease;
}
.reveal-left.visible { opacity: 1; transform: none; }
.d1 { transition-delay: .08s; }
.d2 { transition-delay: .16s; }
.d3 { transition-delay: .24s; }
.d4 { transition-delay: .32s; }
.d5 { transition-delay: .4s; }
.d6 { transition-delay: .48s; }
```

O JavaScript usa `IntersectionObserver` com `threshold:.1` para adicionar `visible`. O observador não remove a classe quando o item deixa a tela: o reveal é efetivamente de entrada, não de ida e volta.

### 8.2 Microinterações

**[EXISTENTE]**

| Elemento | Transição/animação |
|---|---|
| `.btn-red` | Fundo `.2s`; transform `.15s`; sobe `2px` no hover |
| `.btn-outline-dark` | Cor e borda `.2s` |
| `.proj-card` | Borda e transform `.25s`; sobe `4px` no hover |
| `.diff-card` | Fundo `.3s` |
| `nav` | Sombra `.3s` ao receber `.scrolled` após `scrollY>40` |
| Galeria | `transform .4s`; `scale(1.04)` no hover via atributos HTML |
| `.sf-fill` | `width 1.2s cubic-bezier(.4,0,.2,1)`; atraso JS de `300ms` quando observado a `threshold:.3` |
| `#wpp-float` | `wpppulse 2.5s infinite`, com expansão de sombra até `10px` |

**[PENDENTE]** O código analisado não declara `@media (prefers-reduced-motion: reduce)`. Para novas páginas, considerar fallback sem animação e conteúdo legível mesmo se o JavaScript falhar. Não adicionar um mecanismo global sem considerar efeitos nas seções existentes.

---

## 9. Estrutura de conteúdo e convenções de navegação

### 9.1 IDs de seção existentes

A ordem efetiva do HTML recebido é:

1. `#hero` — apresentação principal.
2. `#sobre` — empresa e equipe.
3. `#diferenciais` — atributos competitivos.
4. `#steelframe` — tecnologia e benefícios.
5. `#galeria` — imagens e referências.
6. `#portfolio` — projetos.
7. `#processo` — etapas de atendimento/execução.
8. `#blog` — artigos e conteúdos.
9. `#depoimentos` — relatos de clientes.
10. `#contato` — dados de contato e formulário.

A ordem de links da **barra de navegação** não é idêntica à ordem de todas as seções. `#processo` e `#depoimentos` não têm itens próprios no menu superior.

### 9.2 SEO, idioma e metadados

**[EXISTENTE]**

- Documento com `<html lang="pt-BR">`, `<meta charset="UTF-8">` e viewport responsivo.
- `<title>` orientado a RP2, Steel Frame e alto padrão.
- Metatags `description`, `keywords`, Open Graph básico (`og:title`, `og:description`, `og:type`).
- URL canônica do site: `https://rp2engenharia.com.br` no documento original.
- Bloco JSON-LD `LocalBusiness` descrevendo a empresa e sua localização.

**[RECOMENDADO]** Cada nova página deverá ter `<title>`, descrição, URL canônica e Open Graph **específicos** quando a URL pública definitiva for conhecida. Não duplicar cegamente o canonical da home em Cabanas. Não inventar rotas, domínio de homologação ou URLs de publicação.

---

## 10. Contrato de implementação — futura página “Cabanas Steel Frame”

Esta seção é **[RECOMENDADO]**. Ela orienta a futura solicitação ao Codex; **nenhuma página foi criada** nesta rodada.

### 10.1 Diretrizes obrigatórias

1. Trabalhar somente em `feat/cabanas-steel-frame`.
2. Localizar o HTML principal versionado no repositório, revisar o menu e identificar o mecanismo real de publicação antes de decidir caminho/URL.
3. Incluir no menu superior um item com o nome aprovado para a página, preservando os demais itens e o CTA.
4. Definir nome/caminho do novo arquivo HTML em coerência com a estrutura real do repositório e hospedagem. Exemplo **proposto, não confirmado**: `cabanas-steel-frame.html`.
5. Manter as duas famílias tipográficas, os 13 tokens de `:root`, o padrão de heading/eyebrow, botões, cards e espaçamentos, inclusive no rodapé.
6. Criar layout responsivo para a página; não reproduzir a ausência de navegação mobile como se fosse um requisito de marca.
7. Em páginas secundárias, links de volta às seções da home devem apontar para o arquivo/rota reais da home (por exemplo, `ARQUIVO_DA_HOME.html#sobre` **apenas após confirmação do nome**), não usar `#sobre` se essa seção não existir localmente.
8. Conferir caminhos relativos de CSS, imagens, páginas e âncoras em navegação direta e refresh.
9. Nunca alterar textos comerciais, custos, prazos, fotos ou comprovações de obras sem informação aprovada pelo responsável.
10. Não modificar fora do escopo: formulários, número do WhatsApp, depoimentos, projetos existentes e lógica do site institucional.

### 10.2 Linguagem visual a preservar

- Estrutura editorial, geometria retangular, contraste forte de títulos escuros/vermelhos.
- Fundos claros intercalados com seções escuras de destaque.
- Hierarquia com Barlow Condensed 700/800 em títulos e Barlow 400 em corpo.
- Botões vermelhos e contornados com interações discretas.
- Fotos grandes, cortes controlados e uso parcimonioso de badges.
- Grid consistente em desktop e reorganização explícita no mobile.

### 10.3 Checklist de aceite do trabalho futuro

- [ ] A branch correta foi confirmada (`git branch --show-current`).
- [ ] O menu desktop mostra o novo item e todos os links anteriores continuam funcionando.
- [ ] Existe uma solução navegável para o menu mobile ou limitação foi explicitamente reportada (não ocultar o link como único acesso).
- [ ] A nova página abre diretamente pelo caminho estabelecido, sem depender de navegar primeiro pela home.
- [ ] Tipografia, cores e componentes respeitam os valores deste documento.
- [ ] CTA e navegação de retorno funcionam na nova página.
- [ ] Sem overflow horizontal evidente em 1440/1024/960/768/600/390/320 px.
- [ ] Imagens autorizadas, responsivas e com descrições alternativas apropriadas.
- [ ] Animações não tornam conteúdo indisponível e consideram redução de movimento.
- [ ] Metadados da nova página são específicos e consistentes com a URL definitiva.
- [ ] Mudanças limitadas aos arquivos necessários; diff revisado antes de commit/push.

---

## 11. Pendências observadas e melhorias possíveis

Esta lista **não é uma ordem de implementação**. São pontos técnicos a avaliar somente quando fizerem parte do escopo.

| Prioridade relativa | Situação observada | Possível tratamento futuro |
|---|---|---|
| Alta para nova página | Links da navegação desaparecem até 960px | Menu mobile acessível/alternativa adequada |
| Alta para nova página | Âncoras foram escritas para página única | Links entre páginas usando caminhos reais |
| Alta para nova página | HTML original concentra CSS/JS/imagens | Definir reutilização e organização mínima sem refatorar tudo |
| Média | 199 elementos com `style` inline | Extrair padrões recorrentes quando houver benefício claro |
| Média | Galeria mantém grade inline de 4 colunas | Corrigir responsividade em uma wave autorizada |
| Média | Formulário não inclui e-mail no texto enviado | Revisar regra de negócio se o formulário for alterado |
| Média | Transições sem tratamento de movimento reduzido | Adicionar `prefers-reduced-motion` de forma testada |
| Média | Foco do formulário é visualmente baseado em borda | Verificar navegação por teclado e contraste dos estados |
| Média | Tags de navegação e links externos | Validar foco, `rel` seguro e semântica de navegação |
| Baixa | Sem tokens CSS próprios para spacing/tipografia | Propor tokens derivados apenas se refatoração for aprovada |

### Restrições contra interpretação equivocada

- Este inventário é do **arquivo recebido**, não uma verificação de produção, da hospedagem ou do conteúdo atual do GitHub.
- “Design System” aqui significa **documentação dos padrões existentes + orientações claras de reutilização**. Não há biblioteca de componentes instalável.
- Os exemplos marcados **[RECOMENDADO]** não devem ser confundidos com HTML existente; mantenha o código real como fonte de verdade durante a implementação.
- Alterações futuras no site devem atualizar este documento **somente após** os novos valores serem incorporados e validados.

---

## 12. Prompt-base para o Codex utilizar o Design System

Copiar e adaptar conforme a tarefa:

```text
Trabalhe no repositório engpedroraguzzoni-blip/rp2engenharia, na branch feat/cabanas-steel-frame.

Antes de qualquer alteração:
1. Confirme a branch, o git status, a estrutura e o arquivo HTML principal real.
2. Leia docs/RP2_DESIGN_SYSTEM.md e compare com o CSS do projeto.
3. Diferencie regras [EXISTENTE] de propostas [RECOMENDADO]/[PENDENTE].

Objetivo desta rodada: [DESCREVER OBJETIVO].

Restrições:
- Preservar a identidade visual da RP2 (cores, fontes, tipografia, componentes).
- Não introduzir frameworks/bundlers nem refatorar partes não relacionadas.
- Não alterar a branch main, não criar commit nem realizar push sem autorização.
- Validar desktop/mobile, links e caminhos relativos.
- Não inventar fotos, dados comerciais nem URLs de publicação.

Ao final, entregue:
- Lista de arquivos alterados e motivo.
- Resumo do que foi feito.
- Verificações e testes realizados, com limitações explícitas.
- Pendências e eventuais decisões que dependem de aprovação.
```

---

## 13. Aplicação na página Cabanas — P2.1 aprovada

Esta seção registra como a identidade RP2 foi aplicada à nova página Astro em `cabanas/`. As regras extraídas do HTML institucional continuam identificadas como estado existente daquele arquivo; os detalhes abaixo descrevem a implementação aprovada da P2.1.

- **Logo:** arquivo `cabanas/public/images/branding/logo RP2.png`, apresentado em superfície branca para leitura sobre a Hero.
- **Tipografia:** Barlow Condensed nos títulos e ações; Barlow no texto de apoio. A prévia automatizada usou fontes de reserva quando o Google Fonts não carregou; conferir a fonte real quando avaliar ambiente com acesso às fontes.
- **Abertura:** vídeo `cabanas/public/videos/hero.mp4`, poster `cabanas/public/images/hero/hero-poster.png` e composição desktop/mobile conforme a implementação. A imagem fonte `cabanas/Hero-1.png` permanece preservada.
- **Overlay:** preto com opacidade base de 60% e gradientes adicionais para manter a leitura do texto; o texto vermelho da Hero foi amostrado em pelo menos 3,5:1 no conjunto de frames e viewports documentado no checkpoint de validação. Isso é registro desta composição, não novo token global.
- **Cabeçalho:** transparente sobre a Hero no topo; ao rolar, fundo claro translúcido, texto escuro e sombra/borda discretas. No mobile, o rótulo central é ocultado e permanecem logo e CTA.
- **Ações:** botões RP2 vermelhos com rótulos funcionais para WhatsApp institucional. Não há links para seções futuras até que existam destinos reais.
- **Movimento:** abertura CSS sequencial de aproximadamente 920 ms. Com `prefers-reduced-motion: reduce`, o vídeo permanece no poster e o conteúdo aparece diretamente. Foco por teclado revela o contêiner animado.
- **Cards informativos:** omitidos na P2.1 por não haver benefícios aprovados para exibir.

Evidências visuais e limites dos testes automatizados estão em `docs/previews/p2.1-c/` e `docs/previews/hero-opening/`; o aceite visual final foi feito pelo responsável no navegador. Essas regras de aplicação não alteram tokens canônicos nem descrevem comportamento já existente no HTML institucional.

## 14. Histórico documental

| Versão | Data | Alteração |
|---|---|---|
| 1.0 | 13/10/2026 | Extração inicial de tokens, tipografia, componentes, layout, responsividade, interações e contrato de uso para próximas páginas, a partir do HTML fornecido. |
| 1.1 | 14/10/2026 | Registro da aplicação aprovada do Design System RP2 na Hero e no cabeçalho da página Cabanas. |

**Fim do documento.**
