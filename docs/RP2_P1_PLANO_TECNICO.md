# RP2 Engenharia — Plano Técnico P1: Preparação do Site de Cabanas

**Status:** PLANEJADO — não executado  
**Data:** 13/10/2026  
**Repositório:** `engpedroraguzzoni-blip/rp2engenharia`  
**Branch obrigatória:** `feat/cabanas-steel-frame`  
**Hospedagem informada:** Vercel  
**Endereço público definitivo:** INDEFINIDO  
**Documento visual:** `docs/RP2_DESIGN_SYSTEM.md` (confirmar presença no repositório)  
**Executor previsto:** Codex no VS Code, trabalhando sobre o clone local.

## 1. Objetivo

Preparar uma aplicação independente para a futura área comercial de **Cabanas Modulares em Steel Frame**, dentro do mesmo repositório, **sem alterar o HTML institucional existente**, sem criar ainda o link do menu, sem concluir o desenho da página de vendas e sem modificar o projeto de produção da Vercel.

Entrega P1: diagnóstico do repositório e deploy atual; aplicação Astro + TypeScript + Tailwind CSS em `cabanas/`; estrutura mínima de arquivos, tokens visuais iniciais e uma página provisória funcional; validação de execução/build local; registro de pendências de hospedagem e URLs.

## 2. Decisões e limites

### Congeladas para P1
- Desenvolver **somente** na branch `feat/cabanas-steel-frame`.
- Preservar o arquivo HTML original byte a byte: não renomear, mover, formatar, minificar, editar nem convertê-lo.
- Não modificar a `main`, não fazer merge, commit, push, pull request ou deploy sem autorização posterior.
- Não adicionar o link "Cabanas Modulares" ao menu nesta fase.
- Não tocar em domínios, DNS, configurações de produção da Vercel ou redirects/rewrites já em uso.
- Não introduzir React, SSR, banco de dados, CMS, serviços pagos ou backend sem necessidade concreta identificada.
- Usar o Design System existente como referência de identidade, sem confundir recomendações com estilos já implementados.

### Escolhas técnicas para preparação
- **Astro**: aplicação estática por padrão, com roteamento por arquivos e componentes `.astro`.
- **TypeScript**: modo estrito, de acordo com as configurações disponibilizadas pelo gerador e a versão instalada.
- **Tailwind CSS 4**: integração atual via plugin do Vite usando o comando oficial do Astro. Não adicionar `@astrojs/tailwind` legado.
- **npm**: um único gerenciador de pacotes para a aplicação `cabanas/`, com `package-lock.json` próprio.
- **Sem React na P1**. Só instalar quando algum componente da P3 realmente exigir interatividade avançada.
- **Saída estática** (`output: 'static'`, quando necessário declarar explicitamente); sem adapter SSR para Vercel na P1.
- **Caminho-base inicial de desenvolvimento `/`**, sem `base: '/cabanas'` prematuro; revisar após a decisão de URL pública.

## 3. P1.1 — Diagnóstico inicial (somente leitura)

1. Confirmar diretório raiz, branch e árvore limpa (ou documentar alterações preexistentes):
   ```powershell
   git rev-parse --show-toplevel
   git branch --show-current
   git status --short
   git remote -v
   git log -1 --oneline
   ```
2. Listar apenas arquivos versionados relevantes para o site e deploy:
   ```powershell
   git ls-files
   git ls-files '*vercel*' '*package.json' '*lock*' '*.html' 'docs/*' '.github/*'
   ```
3. Identificar o **nome real** do HTML principal; não presumir que o nome do arquivo anexado ao ChatGPT seja o nome versionado.
4. Verificar se já existe `cabanas/`, `package.json`, `vercel.json`, `.vercel/`, `README`, `.gitignore`, workflows ou estrutura de monorepo. Não sobrescrever nada.
5. Ler o HTML principal, especialmente cabeçalho/navegação, CSS, âncoras e links relativos. Comparar a identidade visual com `docs/RP2_DESIGN_SYSTEM.md`, caso presente.
6. Verificar README/configuração versionada e, se houver acesso autorizado à Vercel, **somente consultar**: Project Name, Root Directory, Framework Preset, Build Command, Output Directory, Production Branch e domínios. Não afirmar valores que não pôde observar.
7. Detectar se a publicação atual serve arquivos estáticos da raiz recursivamente. Registrar o risco de futuros arquivos-fonte de `cabanas/` serem expostos por uma configuração estática ampla. Não mudar deploy nesta etapa.

**Gate P1.1:** relatório factual curto: branch, nome do HTML, estrutura, mecanismo de publicação confirmado ou desconhecido, estado inicial do Git, arquivos protegidos e riscos.

## 4. P1.2 — Definição da arquitetura isolada

Estrutura-alvo mínima (ajustar sem sobrescrever arquivos existentes):

```text
rp2engenharia/
├── <HTML_INSTITUCIONAL_EXISTENTE>   # intocado
├── docs/
│   └── RP2_DESIGN_SYSTEM.md         # documento guia já elaborado
└── cabanas/
    ├── public/
    │   └── images/
    ├── src/
    │   ├── components/
    │   ├── data/
    │   ├── layouts/
    │   │   └── BaseLayout.astro
    │   ├── pages/
    │   │   └── index.astro
    │   └── styles/
    │       └── global.css
    ├── astro.config.mjs
    ├── package.json
    ├── package-lock.json
    ├── tsconfig.json
    └── .gitignore                   # se necessário; sem .git aninhado
```

- Não criar workspaces ou `package.json` na raiz sem evidência de necessidade.
- O site antigo permanece uma aplicação separada, não importada para Astro.
- Componentes e dados futuros ficarão dentro de `cabanas/` e não deverão depender de caminhos fora desse diretório em produção, salvo estratégia de build documentada.
- `docs/` é referência documental. Para build com `Root Directory = cabanas`, não pressupor acesso automático a arquivos externos.

**Gate P1.2:** estrutura confirmada, com isolamento inequívoco entre o HTML original e Astro.

## 5. P1.3 — Inicialização do Astro e Tailwind

1. Verificar pré-requisitos no terminal local:
   ```powershell
   node --version
   npm --version
   ```
   Utilizar Node.js em versão compatível com a documentação da versão efetivamente instalada do Astro (a documentação consultada em 13/10/2026 indica `>= 22.12.0`).
2. Na raiz do repositório, iniciar o scaffolding oficial:
   ```powershell
   npm create astro@latest
   ```
   Selecionar `./cabanas` como destino, o template mínimo, TypeScript estrito e npm. **Não iniciar outro repositório Git dentro de `cabanas/`**. Se o gerador oferecer inicializar Git, escolher não.
3. Dentro de `cabanas/`, adicionar Tailwind 4 com integração atual:
   ```powershell
   cd cabanas
   npx astro add tailwind
   ```
   Confirmar as versões e os arquivos modificados pelo assistente. Não instalar integração de Tailwind 3.
4. Usar CSS global para declarar os tokens institucionais e importá-lo no layout comum; tokens devem vir literalmente do Design System. Não redesenhar estilos do site existente.
5. Manter dependências enxutas. Não instalar React, biblioteca de ícones, bibliotecas de animação ou plugins de SEO nesta fase, salvo exigência real do scaffold.
6. Certificar-se de que há `.gitignore` cobrindo `node_modules/`, `dist/`, `.astro/`, `.vercel/` e segredos, sem ignorar `package-lock.json`.

**Gate P1.3:** dependências instaladas, Astro/Tailwind configurados corretamente, nenhuma mudança fora da pasta nova e de documentação autorizada.

## 6. P1.4 — Estrutura visual mínima

- `BaseLayout.astro` com HTML semântico, `lang="pt-BR"`, viewport, metatags iniciais e import de `global.css`.
- `global.css` com tokens de cores idênticos ao HTML existente e carregamento de fontes `Barlow` e `Barlow Condensed`; evitar estilos globais que provoquem vazamento visual em futura integração.
- `index.astro` apenas com cabeçalho/texto provisórios: “RP2 Engenharia — Cabanas Modulares” e “Página em desenvolvimento”, com visual simples coerente com os tokens.
- Uma rota `/` local válida. **Não criar catálogo, preço, modelos, imagens supostamente oficiais, WhatsApp de vendas, cards finais, hero comercial ou páginas de produtos nesta fase.**
- Não fixar URL canônica pública, não gerar `sitemap` definitivo nem endereços absolutos dependentes do formato de publicação.
- Registrar que o link de navegação da página institucional será tratado em P4, quando existir destino publicado e validado.

**Gate P1.4:** página provisória navegável sem erros e coerente com os tokens, mas sem conteúdo comercial fictício.

## 7. P1.5 — Preparação para Vercel, sem deploy

A Vercel suporta múltiplos projetos vinculados ao mesmo repositório, cada qual com seu **Root Directory**. Para uma futura implantação isolada, planejar um novo projeto com `Root Directory = cabanas` (ainda **não criar** nem configurar na P1 sem autorização explícita). Astro estático não exige adapter SSR. Fontes: documentação oficial de monorepos da Vercel e guia Astro para Vercel.

### Caminhos públicos ainda possíveis

| Alternativa | Vantagem | Atenção operacional | Decisão P1 |
|---|---|---|---|
| `cabanas.rp2engenharia.com.br` | Separação de app e deploy bastante clara | DNS/domínio do novo projeto e consistência de navegação | Possível, não configurar |
| `rp2engenharia.com.br/cabanas/` | Experiência sob o mesmo domínio | Exige estratégia de roteamento/rewrite/proxy ou arquitetura de deploy compatível, cuidado com `base`, assets e URLs absolutas | Possível, não configurar |
| Domínio independente | Autonomia de marketing | Compra/configuração, SEO e navegação entre marcas | Possível, não configurar |

**Não presumir que configurar Root Directory `cabanas` cria automaticamente a URL `/cabanas/` no domínio do site antigo.** São operações distintas. Rewrites externos podem encaminhar uma subrota para outro projeto, mas exigem configuração e testes de paths/assets. Não criar um `vercel.json` na raiz nem rewrites em produção antes da escolha.

Registrar, quando houver acesso, se o HTML atual é publicado por framework `Other`, por arquivo `index.html`, configuração de saída específica ou outra estratégia. Não converter o projeto existente.

**Gate P1.5:** memorando de deploy futuro com fatos confirmados, dúvidas abertas e indicação explícita de que nenhuma alteração foi feita na Vercel.

## 8. P1.6 — Gates técnicos e entrega

Executar dentro de `cabanas/`:

```powershell
npm run build
npm run dev
```

- Verificar no navegador que a página provisória carrega sem erros visíveis, no desktop e em largura mobile.
- Se houver comando de checagem TypeScript (`astro check`) configurado, rodá-lo; caso não exista, registrar isso em vez de declarar gate inexistente como aprovado.
- Verificar que a saída de build é estática e que `dist/` não foi incluído no versionamento.
- Na raiz do repositório:
  ```powershell
  git status --short
  git diff --check
  git diff -- <HTML_INSTITUCIONAL_EXISTENTE>
  git status --short -- <HTML_INSTITUCIONAL_EXISTENTE>
  ```
- Para garantir a imutabilidade do HTML mesmo se houver renomeação não detectada em diffs, comparar o blob original em `HEAD` com o arquivo atual, ou hash equivalente, e comprovar que continua versionado no mesmo caminho.
- Atenção: `git diff` sozinho não lista arquivos novos; conferir `git status --short` e a lista completa de arquivos novos.
- Confirmar que não existe `.git` aninhado em `cabanas/`, nem segredos ou `node_modules` versionados.
- Produzir relatório final com árvore sucinta, scripts, versões, gates e todas as pendências.
- **Não realizar commit, push, PR ou deploy automaticamente.** Deixar essas ações para uma autorização posterior.

### Critérios de aceite P1

- [ ] Branch correta confirmada.
- [ ] Estado inicial do repo documentado.
- [ ] Arquivo institucional identificado e comprovadamente intacto.
- [ ] Hospedagem existente investigada dentro do nível de acesso permitido; desconhecidos identificados.
- [ ] `cabanas/` é aplicação Astro independente, sem Git aninhado.
- [ ] TypeScript e Tailwind 4 operacionais.
- [ ] Design System consultado e tokens iniciais preservados.
- [ ] `npm run build` aprovado.
- [ ] Prévia local de `/` aberta, com verificação básica mobile.
- [ ] URL pública não decidida/forçada e Vercel não modificada.
- [ ] Nenhuma alteração no HTML original, na `main`, no menu ou na produção.
- [ ] Diff e relatório apresentados para revisão humana.

## 9. Fora de escopo (waves posteriores)

- **P2:** arquitetura visual definitiva, componentes reutilizáveis, header/footer e identidade da área Cabanas.
- **P3:** páginas comerciais, catálogo/modelos, galerias, formulário/orçamento, conteúdo validado e SEO final.
- **P4:** decidir URL e deploy; configurar Vercel/DNS/roteamento; adicionar **um único link** no menu do HTML institucional, testar navegação, revisar e publicar.

## 10. Prompt de execução sugerido para o Codex

> Você está no clone local do repositório `engpedroraguzzoni-blip/rp2engenharia`. Execute somente a **P1 — Preparação do Site de Cabanas**, conforme `RP2_P1_PLANO_TECNICO.md` e `docs/RP2_DESIGN_SYSTEM.md`, se esses documentos estiverem disponíveis. Trabalhe exclusivamente na branch `feat/cabanas-steel-frame`; verifique isso antes de qualquer escrita. Identifique primeiro o nome real do arquivo HTML institucional e faça um inventário do Git, do site atual e de eventuais arquivos Vercel. Não altere, mova, renomeie, formate ou substitua o HTML institucional, nem crie o link do menu. Crie uma aplicação isolada em `cabanas/` usando Astro estático, TypeScript estrito e Tailwind CSS 4 pela integração moderna. Não inicialize outro Git, nem adicione React, SSR, backend, biblioteca desnecessária ou configuração de domínio. Reproduza os tokens do Design System em `src/styles/global.css` e crie apenas uma página provisória com layout básico e sem conteúdo comercial inventado. A hospedagem é Vercel, mas o endereço final ainda não foi definido: não crie redirects, rewrites, `base` para `/cabanas` nem configure a Vercel. Rode build e validações locais; comprove que o arquivo HTML original não mudou, inspecione arquivos novos e informe os riscos de deploy. Ao terminar, entregue relatório de diagnóstico, arquivos criados, comandos/resultados, pendências e `git status`. **Não faça commit, push, PR ou deploy.** Se houver arquivos preexistentes, incompatibilidades ou informação de hospedagem inacessível, preserve tudo e explicite a limitação; não invente os dados.

## 11. Referências oficiais consultadas

- Astro: https://docs.astro.build/en/guides/deploy/vercel/
- Astro: https://docs.astro.build/en/guides/styling/
- Astro: https://docs.astro.build/pt-br/install-and-setup/
- Vercel monorepos: https://vercel.com/docs/monorepos
- Vercel monorepo FAQ: https://vercel.com/docs/monorepos/monorepo-faq
- Vercel rewrites: https://vercel.com/docs/routing/rewrites
