# RP2 Engenharia — Runbook Operacional | Site de Cabanas Modulares

**Versão:** 2.2 — execução incremental da P2  
**Data-base:** 14/10/2026  
**Status:** EM ANDAMENTO — P2.1 aprovada em 14/10/2026; P2.2 é a próxima wave, aguardando autorização de execução  
**Repositório:** `engpedroraguzzoni-blip/rp2engenharia`  
**Branch de trabalho:** `feat/cabanas-steel-frame`  
**Aplicação:** `cabanas/` — Astro estático + TypeScript estrito + Tailwind CSS 4  
**Site institucional existente:** `https://rp2engenhariasteelframe.com.br/`  
**Destino deste arquivo:** `docs/RP2_CABANAS_RUNBOOK_OPERACIONAL.md`  
**Próxima wave:** **P2.2 — apresentação RP2 Cabanas e proposta de valor**, aguardando autorização de execução

> **Como usar:** este é o documento **operacional ativo**. O responsável aprova planejamento, textos, mídias, resultado visual e avanço de etapa; o Codex executa exclusivamente a wave autorizada no repositório local. Construir **uma seção por vez**; refinamentos pertencem à mesma wave. Checkboxes indicam critérios a cumprir, **não** autorização para executá-los todos. Nenhum commit, push ou deploy é automático.

---

## 1. Estado inicial e premissas aprovadas

| Assunto | Premissa operacional |
|---|---|
| P1 — preparação técnica | Concluída **conforme relatório anterior do Codex**; confirmar somente o estado local necessário, sem reinstalar nem refazer P1 |
| Stack | Preservar Astro, TypeScript estrito, Tailwind CSS 4 e npm da aplicação `cabanas/` |
| Produto/site | Home **institucional e comercial** da linha de Cabanas Modulares RP2; não uma landing page exclusiva da Siena |
| Modelos | **Três cabanas previstas**; somente a **Cabana Siena** possui dados técnicos/comerciais recebidos até esta data |
| Abertura | Hero institucional com vídeo fornecido, logomarca RP2 e composição orientada pelas referências visuais fornecidas pelo responsável |
| Cabeçalho | Menu superior **flutuante e persistente durante a rolagem**; integra a P2.1 desde o início |
| Construção | Uma wave por vez, com avaliação e refinamento visual antes do aceite |
| Site institucional | HTML atual preservado; integração e novo endereço somente na fase P4 |
| Repositório local | Preservar arquivos rastreados, modificados e não rastreados; o estado de Git deve ser observado antes de cada execução |
| Publicação | URL definitiva, Vercel, DNS e integrações de produção ainda sem autorização nesta fase |

**Não criar nomes, imagens, descrições, preços, medidas ou cartões de modelos ainda não documentados.** A previsão de três modelos não equivale a ter três produtos aprovados para exibição.

### 1.1 Hierarquia das fontes

1. **Design e marca:** `docs/RP2_DESIGN_SYSTEM.md` — tokens, fontes, cores, estilo e componentes.
2. **Dados dos produtos:** `docs/RP2_CABANA_SIENA_FICHA_TECNICA_COMERCIAL.md` e futuras fichas oficiais aprovadas.
3. **Arquitetura técnica:** `docs/RP2_P2_PLANO_TECNICO_INCREMENTAL.md` — **v1.0**, documento técnico ativo da P2.
4. **Execução, gates e estados:** **este runbook**.
5. **Histórico:** `docs/RP2_P1_PLANO_TECNICO.md` e `docs/RP2_P2_PLANO_VISUAL_FUNCIONAL.md`; não funcionam como filas paralelas da P2.
6. **Referências visuais:** sites Nature Haus e Atualle, capturas `hero-01.png`/`menu-flutuante.png` da Nature Haus e captura `hero-rp2.png`, fornecidas/indicadas pelo responsável; usar para orientar composição e comportamento, não como ativos de produção.

Se um arquivo previsto não estiver no clone local, registrar essa ausência e solicitar o material pertinente; não substituir silenciosamente a fonte. Em divergências, fatos comerciais seguem a ficha atual aprovada, identidade segue o Design System, arquitetura segue o plano técnico e sequência segue este runbook.

### 1.2 Limites permanentes da P2

- Não alterar, converter, mover, formatar ou renomear o HTML institucional existente.
- Não operar na `main`, fazer merge/PR, commit, push, deploy, alterar DNS, Vercel, domínio, `base`, redirecionamentos ou rewrites sem autorização explícita.
- Não executar `git add .` automaticamente; não limpar arquivos não rastreados, descartar mudanças nem substituir assets originais.
- Não adicionar frameworks, bibliotecas de animação, CMS, SSR, banco, checkout, simulador ou formulários de coleta sem requisito e aprovação específicos.
- Não publicar imagens, logotipos, textos, código ou capturas da Nature Haus; não apresentar vídeo conceitual/gerado por IA como foto ou registro de obra entregue.
- Não criar funcionalidades decorativas sem ação: links `#` vazios, âncoras inexistentes, telefone inventado ou botão que não faz nada.
- Não inventar condições comerciais, métricas de desempenho, prazos, garantias, personalização integral, economia ou quantidade de ambientes.

---

## 2. Regras comerciais — fonte de dados e publicação

A Hero é **institucional** e, por padrão, **não exibe nome, metragem ou preço de um modelo específico**. Preços e detalhes de produto entram nas seções próprias da Home, após conferência editorial.

### 2.1 Siena — dados conhecidos

| Campo | Referência atual |
|---|---|
| Modelo | Cabana Siena |
| Área | 26 m² |
| Sistema construtivo | Steel Frame |
| Kit para montagem | **A partir de R$ 59.970,00** |
| Cabana pronta — composição inicial | **A partir de R$ 164.000,00** |
| Relação entre modalidades | O valor de referência da cabana pronta **já inclui o kit** |
| Fundação prevista na composição | Radier |
| Revestimentos/acabamentos citados | WPC em áreas secas; PVC decorativo no banheiro |
| Fachada e cobertura citadas | Telha EPS na fachada; telha PIR na cobertura |

**Obrigatório nas waves comerciais:** conferir a ficha da Siena e a proposta original. Não somar valores do kit e da cabana pronta, nem tratar R$ 164.000,00 como preço fechado de empreitada “chave na mão”. A modalidade pronta é uma **composição de referência**, sujeita a verificação de quantitativos e cotações locais. Frete, gestão de obra, terreno, taxas, mobiliário, eletrodomésticos, seguro e reserva de imprevistos foram identificados como itens fora da proposta; conferir a redação vigente antes de publicar. Não presumir que fundação, cobertura, esquadrias, instalações e mão de obra estão incluídas no **kit**.

O texto completo das ressalvas e a vigência dos preços exigem confirmação antes da publicação. Valores exibidos no site deverão permanecer associados à modalidade correta e a uma fonte única de dados, quando implementada.

### 2.2 Outros dois modelos

- [ ] Receber nomes, fichas, imagens autorizadas e política comercial de cada modelo.
- [ ] Conferir dados de cada cabana independentemente da Siena.
- [ ] Autorizar individualmente a publicação; não criar registros fictícios para preencher posições no catálogo.

Esses itens são **dependências editoriais futuras**, não bloqueadores da P2.1. A seção de modelos será adaptada ao conteúdo realmente aprovado quando chegar sua wave.

---

## 3. Processo padrão de execução de cada wave

### 3.1 Entrada — confirmação breve

1. Confirmar raiz do repositório, branch `feat/cabanas-steel-frame` e `git status --short` antes de escrever; preservar todos os arquivos, inclusive não rastreados.
2. Ler somente os trechos pertinentes do **Plano Técnico P2**, do Design System e da ficha comercial necessária. Não executar diagnóstico extenso já realizado na P1.
3. Verificar se o que será implementado já existe ou foi **absorvido** por alguma wave anterior. Não duplicar componentes ou repetir código resolvido.
4. Identificar os arquivos que precisará tocar. Se o trabalho extrapolar a wave, parar e pedir autorização.

### 3.2 Implementação e revisão visual

5. Implementar apenas a seção autorizada e a infraestrutura estritamente indispensável para fazê-la funcionar.
6. Priorizar componentes Astro e padrões atuais de CSS/Tailwind; usar JavaScript cliente apenas quando justificar interação real.
7. Utilizar somente mídias e informações fornecidas/aprovadas; não modificar originais sem autorização.
8. Validar links de fato existentes. Se a próxima seção ainda não existe, **não criar uma âncora falsa** para antecipá-la.
9. Apresentar prévia no navegador. Ajustar visual dentro da **mesma** wave até obter aprovação do responsável.

### 3.3 Gate e saída

10. Dentro de `cabanas/`, executar `npm run check` e `npm run build` ao fechar uma rodada significativa e obrigatoriamente antes do aceite da wave. Registrar falhas de scripts, se inexistentes, em vez de declarar sucesso fictício.
11. Na raiz do repositório, revisar `git diff --check`, `git status --short`, arquivos novos/não rastreados e o diff do HTML institucional pelo **caminho real** (sem supor nome de arquivo).
12. Conferir a seção em aproximadamente **1440 px, 768 px e 390 px** (desktop/tablet/mobile); navegação por teclado, contraste, overflow, media e CTAs conforme a wave. Usar teste visual automatizado se disponível; caso contrário, pedir avaliação manual.
13. Relatar **apenas** alterações, testes, resultado visual, pendências concretas e pedido de aprovação. Não gerar documentação extensa a cada ajuste.
14. Atualizar o checkpoint desta wave no runbook após o aceite. Só iniciar a próxima quando houver **aprovação explícita**.

**Política de Git:** nenhuma wave inclui commit, push, PR ou deploy por padrão. Antes do primeiro commit autorizado, inspecionar assets grandes, originais e arquivos privados para evitar versionamento indevido.

### 3.4 Modelo breve de checkpoint

```md
### Checkpoint P2.X
- Estado: PENDENTE | EM EXECUÇÃO | AGUARDANDO APROVAÇÃO | APROVADA | BLOQUEADA | ABSORVIDA
- Entrega: ...
- Arquivos alterados / novos: ...
- Gates: check ...; build ...; diff/status ...
- Visual: desktop ...; tablet ...; mobile ...
- Site institucional: preservado? ...
- Pendências concretas: ...
- Aceite do responsável: ...
```

`ABSORVIDA` requer evidência da implementação existente cobrindo o critério; não significa apenas “parece desnecessária”. Não reabrir uma wave aprovada sem motivo técnico/editorial real.

---

## 4. P2 — Waves operacionais

A P2 começa **diretamente na P2.1**. Não há wave P2.0 independente obrigatória: localizar arquivos, conferir dados e avaliar direitos de mídia acontecem **sob demanda** na wave que utiliza cada material. Não executar inventário fotográfico geral antes da Hero.

### P2.1 — Hero institucional + menu flutuante

**Objetivo:** apresentar a RP2 Engenharia e sua linha de Cabanas Modulares em uma abertura cinematográfica baseada no vídeo fornecido, com identidade RP2 e menu persistente durante a rolagem. **Não transformar a Hero em apresentação da Siena.**

**Arquivos de mídia esperados (confirmar nomes reais):**

```text
cabanas/public/videos/hero.mp4
cabanas/public/images/branding/logo RP2.png
cabanas/public/images/hero/hero-poster.png  # derivado de cabanas/Hero-1.png; original preservado
```

Os caminhos acima foram confirmados na implementação da P2.1. A imagem de inspiração Nature Haus permanece material de consulta, não asset de produção.

#### P2.1-A — Implementação inicial

- [x] Confirmar branch, Git status, estrutura Astro e caminhos reais de vídeo/logomarca; não alterar arquivos fora do escopo.
- [x] Consultar capturas da Hero e do menu flutuante fornecidas pelo responsável e os tokens/fontes do Design System RP2.
- [x] Implementar vídeo de fundo decorativo com `autoplay`, `muted`, `loop` e `playsinline`, enquadramento `object-fit: cover` e overlay de contraste.
- [x] Integrar a logomarca oficial e o cabeçalho com comportamento persistente no scroll: **sobreposto à Hero no topo; barra legível sólida/translúcida ao rolar**, sem mudança brusca de layout.
- [x] Preparar navegação desktop e comportamento mobile; apresentar **somente links/CTAs com destinos existentes e verificados**.
- [x] Criar título e apoio **institucionais** com copy proposta para aprovação; não colocar nome/preços/metragem da Siena na chamada principal.
- [x] Criar a primeira composição responsiva (texto à esquerda no desktop, destaque da paisagem, ações úteis quando validadas).
- [x] Não construir seção de modelos, cards de produto, preços, galeria, FAQ ou rodapé definitivo.

**Saída A:** primeira prévia navegável para avaliação. Não exige que detalhes decorativos estejam aprovados.

#### P2.1-B — Refinamento visual

- [x] Avaliar a Hero real em navegador e comparar **composição**, não identidade de marca, com as capturas de referência.
- [x] Ajustar tamanho/hierarquia do título, overlay, fontes, espaçamento, áreas vazias, recorte do vídeo e posição dos botões.
- [x] Refinar a aparência e o comportamento do header antes/depois da rolagem, evitando colisão com o conteúdo.
- [x] Avaliar cards flutuantes **somente** se houver informação institucional comprovada e aprovação expressa; omitir em caso contrário.
- [x] Revisar copy e rótulos de CTAs com o responsável; eliminar alegações não confirmadas.

**Saída B:** composição visual aprovada ou rodada de ajustes registrada, sem abrir a P2.2.

#### P2.1-C — Responsividade, mídia e acessibilidade

- [x] Conferir 1440/768/390 px: legibilidade, vídeo, logo, navegação, contraste e ausência de rolagem horizontal.
- [x] Testar header fixo/persistente ao rolar, sobre a Hero e em fundo sólido; validar comportamento em mobile e por teclado.
- [x] Testar estados de carregamento/erro de vídeo. Adotar **poster/fallback estático aprovado**; se faltar, solicitar o asset e manter pendência explícita antes do aceite.
- [x] Respeitar `prefers-reduced-motion`; oferecer alternativa estática quando o usuário reduzir animações.
- [x] Conferir foco visível, ordem de tabulação, leitura do `h1`, acessibilidade de menu mobile caso exista e ausência de links falsos.
- [x] Verificar peso do vídeo, carregamento e comportamento em rede/dispositivo lento; **não converter/substituir o original automaticamente**.
- [x] Executar `npm run check`, `npm run build` dentro de `cabanas/`; revisar diff/status e confirmar HTML institucional intocado.

**Saída C:** Hero funcional em desktop/tablet/mobile, com gates técnicos registrados e sem bloqueios conhecidos.

#### P2.1-D — Aceite e checkpoint

- [x] Apresentar versão final com capturas ou instruções para abrir `http://localhost:4321/` (ou a URL indicada por `npm run dev`).
- [x] Receber aprovação visual explícita do responsável sobre vídeo, copy, header, responsividade e CTAs exibidos.
- [x] Registrar checkpoint curto: entrega, arquivos, gates e eventuais pendências **não bloqueantes**.
- [x] Marcar P2.1 como `APROVADA`; **não iniciar P2.2 automaticamente**.

**Gate P2.1:** Hero institucional com vídeo/logomarca oficiais, cabeçalho que acompanha a rolagem, visual responsivo e acessível, fallback coerente, nenhuma informação inventada, CTAs realmente funcionais, check/build passando, HTML institucional preservado e aceite visual do responsável. A Hero pode ser refinada em menos rodadas se os critérios já estiverem cobertos; não refazer testes sem necessidade.

### P2.2 — RP2 Cabanas: apresentação e proposta de valor

- [ ] Criar uma seção institucional complementar à Hero com texto aprovado sobre a atuação da RP2 no segmento.
- [ ] Usar somente afirmações sustentadas pelo conteúdo institucional e informações confirmadas.
- [ ] Integrar transição visual fluida com a Hero e verificar o header sobre o fundo da seção.
- [ ] Adicionar âncora real para navegação **apenas agora**, se fizer sentido.

**Gate:** apresentação clara, visual desktop/mobile revisado, texto aprovado e header sem regressões.

### P2.3 — Modelos de cabanas

- [ ] Confirmar quais modelos possuem dados/imagens aprovados e quais podem ser mostrados.
- [ ] Criar fonte única de dados e estados editoriais **quando necessário**; não popular catálogo com `modelo-2`/`modelo-3` fictícios.
- [ ] Exibir somente modelos autorizados. A estrutura deve aceitar os três modelos previstos sem inventar conteúdo faltante.
- [ ] Criar âncora e ativar link “Modelos” no header/CTA **após** a seção existir de fato.

**Gate:** modelos apresentados com dados corretos, nenhum card vazio/falso e navegação funcional em mobile/desktop.

### P2.4 — Apresentação e galeria da Cabana Siena

- [ ] Criar seção específica para Siena com 26 m², Steel Frame e descrição aprovada; não projetar detalhes da Siena nas outras cabanas.
- [ ] Selecionar imagens reais ou renders autorizados, com distinção editorial adequada; preservar originais.
- [ ] Produzir derivados otimizados **com autorização**, sem substituir fontes originais.
- [ ] Construir galeria proporcional à quantidade de mídias disponíveis; evitar carrossel complexo sem motivo.

**Gate:** seção e galeria fiéis às imagens/dados aprovados, legíveis e navegáveis; nenhum material da Nature Haus publicado.

### P2.5 — Modalidades de contratação

- [ ] Explicar **kit para montagem** e **cabana pronta** para a Siena conforme a ficha comercial.
- [ ] Separar o que pertence ao kit do que é fornecimento/execução da composição da cabana pronta.
- [ ] Não afirmar contratação “chave na mão” nem extrapolar modalidades para modelos sem ficha.

**Gate:** duas modalidades compreensíveis e comercialmente corretas, redação aprovada.

### P2.6 — Preços de referência e condições

- [ ] Implementar preços da Siena por modalidade, em fonte única, com rótulo **“A partir de”**.
- [ ] Exibir **R$ 59.970,00** (kit) e **R$ 164.000,00** (composição da pronta); **não somar**: pronta já inclui o kit.
- [ ] Aproximar as ressalvas dos valores e oferecer acesso fácil às condições completas.
- [ ] Conferir exclusões, vigência e redação comercial com a ficha e aprovação do responsável.
- [ ] Só incluir preços de outras cabanas se suas políticas específicas tiverem sido aprovadas.

**Gate:** valores e modalidades inequívocos, condições visíveis, sem preço fechado artificial ou alegações indevidas.

### P2.7 — Características técnicas e materiais

- [ ] Apresentar dados tecnicamente documentados de cada modelo, começando pela Siena.
- [ ] Distinguir especificações da composição de itens incluídos no kit.
- [ ] Não inferir quartos, banheiros, áreas adicionais, certificações, desempenho ou prazos a partir das imagens.

**Gate:** conferência técnica concluída e texto aprovado, inclusive em telas menores.

### P2.8 — FAQ

- [ ] Elaborar perguntas somente sobre dados/condições confirmados: preço inicial, inclusão do kit, frete, contratação e orçamento.
- [ ] Responder sem inventar garantias, prazos, área de atendimento ou condições contratuais.
- [ ] Usar solução semântica e acessível (por exemplo, `<details>` e `<summary>`), evitando dependências desnecessárias.
- [ ] Inserir link para contato apenas quando houver canal validado.

**Gate:** respostas corretas, FAQ utilizável com teclado e em mobile, revisão editorial concluída.

### P2.9 — Contato, rodapé e refinamento de navegação

- [ ] Confirmar canal oficial de orçamento e dados de contato antes de criar botão/link correspondente.
- [ ] Implementar CTA final e rodapé com informações institucionais verificadas.
- [ ] Finalizar itens da navegação conforme seções/rotas **efetivamente disponíveis**, reutilizando o header da P2.1 sem refazê-lo.
- [ ] Verificar links externos, menu mobile, foco, navegação por teclado e comportamento fixo em todas as seções.
- [ ] Não alterar o menu do HTML institucional nesta etapa.

**Gate:** contato funcional, rodapé aprovado e navegação consistente, sem links quebrados ou canais fictícios.

### P2.10 — Revisão integrada e fechamento da Home

- [ ] Conferir continuidade visual e jornada **Hero → apresentação → modelos → Siena → modalidades → preços → informações técnicas → FAQ → contato**.
- [ ] Revisar títulos, metadados locais, acessibilidade, contraste, links, responsividade, vídeo, poster e imagens.
- [ ] Testar desktop/tablet/mobile e `prefers-reduced-motion`; corrigir apenas lacunas/regressões reais.
- [ ] Executar gates finais `npm run check`, `npm run build`, `git diff --check` e revisar arquivos não rastreados.
- [ ] Confirmar preservação integral do HTML institucional; registrar só pendências reais e obter aceite final da P2.

**Gate:** Home pronta **localmente**, sem bloqueadores de conteúdo/UX/qualidade conhecidos; **nenhum deploy** nesta wave.

---

## 5. Fases posteriores — somente após aceite da P2

### P3 — Complementos comerciais e expansão sob demanda

- [ ] Receber/validar fichas, imagens e modalidades das outras cabanas; incorporar somente conteúdo autorizado.
- [ ] Revisar textos comerciais definitivos e eventuais fluxos de orçamento/captação com regras de privacidade apropriadas.
- [ ] Avaliar páginas individuais, catálogo mais amplo e recursos adicionais **somente** se houver necessidade concreta.
- [ ] Validar direitos das mídias, vigência de preços e materiais finais antes de publicação.

### P4 — Publicação e integração com o site institucional

- [ ] Definir endereço público: **subdiretório `/cabanas/` ou subdomínio**, com consequências distintas para `base`, assets e roteamento.
- [ ] Verificar configuração real do projeto institucional na Vercel e planejar deploy independente da aplicação Astro.
- [ ] Ajustar domínio/DNS ou rewrites somente após escolher a arquitetura; validar links diretos e refresh.
- [ ] Revisar SEO público, metadados, canonical e imagens sociais depois de fixar URL definitiva.
- [ ] Obter autorização expressa antes de configurar publicação, Git ou produção.
- [ ] Só depois de a página nova estar publicada e validada, inserir **um único link** para Cabanas Modulares na navegação do HTML institucional; preservar o restante e comparar o diff.
- [ ] Validar navegação ida/volta, contato, mobile e plano de reversão.

**Gate P4:** ambiente novo publicado no destino aprovado, site institucional preservado exceto pela integração autorizada e funcionamento verificado.

---

## 6. Critérios gerais de aceite

| Área | Critério |
|---|---|
| Identidade | Design System RP2 aplicado; Nature Haus somente como inspiração de composição |
| Abertura | Hero institucional, vídeo oficial fornecido, logo RP2 e header flutuante persistente |
| Conteúdo | Somente dados sustentados por fichas e decisões aprovadas; três modelos previstos, sem inventar os faltantes |
| Comercial | Preços da Siena por modalidade, ambos “a partir de”; composição pronta **inclui** kit e possui ressalvas |
| Mídia | Originais preservados, direitos confirmados, poster/fallback e redução de movimento tratados |
| Navegação | Links/âncoras existentes, contato oficial confirmado, header e menu mobile acessíveis |
| Responsividade | 1440/768/390 px, legibilidade, foco e ausência de overflow horizontal |
| Qualidade | `npm run check` e `npm run build` passando em `cabanas/`; diffs/arquivos novos inspecionados |
| Segurança de escopo | HTML institucional intacto na P2; Git/Vercel/domínios sem mudanças não autorizadas |
| Governança | Aprovação visual explícita antes de avançar; checkpoints curtos sem retrabalho |

## 7. Quadro de acompanhamento

**Regra:** marcar `APROVADA` somente com implementação verificada e aceite do responsável. `ABSORVIDA` somente com evidência concreta. A D1.2 é revisão documental; **não** altera o estado de nenhuma wave de código.

| Wave | Escopo | Status em 14/10/2026 |
|---|---|---|
| P2.1 | Hero institucional + vídeo + menu flutuante | **APROVADA — 14/10/2026** |
| P2.2 | Apresentação RP2 Cabanas | **PENDENTE — próxima** |
| P2.3 | Modelos de cabanas | PENDENTE |
| P2.4 | Siena e galeria | PENDENTE |
| P2.5 | Modalidades de contratação | PENDENTE |
| P2.6 | Preços e condições | PENDENTE |
| P2.7 | Características técnicas | PENDENTE |
| P2.8 | FAQ | PENDENTE |
| P2.9 | Contato, rodapé e refino do header | PENDENTE |
| P2.10 | QA integrado e fechamento P2 | PENDENTE |
| P3 | Conteúdo/expansão sob demanda | FUTURA |
| P4 | URL, Vercel e integração institucional | FUTURA |

**Após cada wave:** atualizar apenas estado, checkpoint curto e dependências reais para a próxima. Não manter uma segunda tabela de execução em plano técnico ou documentos históricos.

---

## 8. Prompts operacionais para o Codex

> **Uso:** o prompt 8.3 é o modelo atual para waves futuras, sempre após autorização. Os prompts 8.1 e 8.2 foram preservados como histórico da P2.1 aprovada; não reutilizá-los. O Codex não deve executar waves além da solicitada.

### 8.1 Prompt histórico — execução inicial P2.1-A (encerrado)

> Histórico encerrado após o aceite da P2.1 em 14/10/2026. O texto abaixo registra o escopo original e não é uma instrução pendente.


```text
Repositório: engpedroraguzzoni-blip/rp2engenharia
Branch obrigatória: feat/cabanas-steel-frame
Aplicação: cabanas/

Execute SOMENTE P2.1-A do arquivo
  docs/RP2_CABANAS_RUNBOOK_OPERACIONAL.md
usando a especificação P2.1 de
  docs/RP2_P2_PLANO_TECNICO_INCREMENTAL.md.
Consulte também os trechos pertinentes de
  docs/RP2_DESIGN_SYSTEM.md.

Confirme branch, git status, caminhos reais do vídeo em
cabanas/public/videos/ e da logo em cabanas/public/images/branding/.
Preserve todos os arquivos existentes e não rastreados.

Vou fornecer uma captura da Hero e outra do menu persistente
como REFERÊNCIAS DE COMPOSIÇÃO da Nature Haus. Não copie
marca, fotos, textos, cores ou código da referência.

Implemente somente a Hero INSTITUCIONAL da RP2 Cabanas:
- vídeo local de fundo e overlay legível;
- logomarca oficial;
- header flutuante, sobreposto no início e persistente ao rolar,
  com versão de contraste apropriado após a rolagem;
- tipografia, layout e texto inicial coerentes com Design System RP2;
- navegação/CTAs apenas para destinos existentes e confirmados;
- primeira adaptação desktop/tablet/mobile.

A Hero NÃO é da Cabana Siena. Não acrescente modelos fictícios,
preços, seções futuras, galeria, FAQ ou rodapé definitivo.
Se faltar poster aprovado ou contato oficial, registre a pendência;
não invente arquivo, telefone ou âncora.
Não modifique HTML institucional nem Vercel.
Não faça commit, push, PR ou deploy.

Ao concluir, informe arquivos tocados, comandos/resultados,
limitações e URL local para revisão visual. Pare após P2.1-A.
```

### 8.2 Prompt histórico — refinamento P2.1-B/C/D (encerrado)

> Histórico encerrado após o aceite da P2.1 em 14/10/2026. O texto abaixo registra o fluxo original e não é uma instrução pendente.


```text
Continue SOMENTE a P2.1, na branch feat/cabanas-steel-frame.
Leia a seção P2.1 do runbook e do Plano Técnico Incremental.
Use a avaliação visual que vou fornecer como lista de ajustes.
Não recrie componentes que já funcionam e não avance para P2.2.

Corrija apenas os pontos aprovados, preserve originais, teste o
header persistente, vídeo/fallback, responsividade e acessibilidade.
Execute npm run check e npm run build dentro de cabanas/,
revise git diff --check e git status --short, confirme que o HTML
institucional não foi alterado e apresente o resultado visual.
Não faça commit, push ou deploy. Aguarde meu aceite.
```

### 8.3 Template das waves seguintes

```text
Execute SOMENTE a wave P2.[N] de
  docs/RP2_CABANAS_RUNBOOK_OPERACIONAL.md
na branch feat/cabanas-steel-frame.
Consulte o trecho pertinente do Plano Técnico P2,
o Design System e as fichas comerciais aplicáveis.
Antes de codificar, identifique o que já está coberto para
não duplicar trabalho; preserve todos os arquivos existentes.

Implemente apenas a seção autorizada, com dados oficiais,
links reais e respeito aos componentes já aprovados.
Teste desktop/tablet/mobile, npm run check, npm run build,
git diff --check e git status --short; preserve o HTML institucional.
Reporte alterações e pendências. Sem commit, push ou deploy.
Pare e aguarde aprovação antes da próxima wave.
```

---

## 9. Registro de checkpoints e pendências

### Checkpoint documental D1.2 — criação da versão 2.1

- **Tipo:** atualização de documentação operacional; **sem execução de código**.
- **Fonte de arquitetura:** `RP2_P2_PLANO_TECNICO_INCREMENTAL.md`, v1.0 (14/10/2026).
- **Ponto de partida operacional:** P2.1, Hero institucional da linha RP2 Cabanas.
- **Mídia:** vídeo e logomarca fornecidos pelo responsável, a confirmar pelos caminhos reais em `cabanas/public/`; imagens Nature Haus apenas como referência.
- **Cabeçalho:** menu flutuante/persistente já na P2.1, a ser expandido sem duplicação nas waves posteriores.
- **Modelos:** três previstos; somente Siena com ficha disponível até o momento.
- **Estado das waves:** todas PENDENTES; nenhuma implementação atestada por esta atualização documental.
- **Próximo passo:** após revisão/aprovação documental, iniciar a implementação **P2.1-A**, sem antecipar P2.2.

### Checkpoint P2.1 — Hero aprovada

- **Data e aceite:** 14/10/2026; responsável conferiu a versão final no navegador e informou que está aprovada.
- **Entrega:** Hero institucional com vídeo `public/videos/hero.mp4`, logo oficial, poster aprovado, texto com Steel Frame, contatos WhatsApp válidos, sobreposição preta refinada e abertura suave em CSS (920 ms). Header persistente, transparente no topo e claro após rolagem.
- **Gates:** Astro check sem erros/avisos e build estático aprovados. Verificados 1440/768/390 px, teclado/foco, hover, falha/carregamento lento do vídeo, redução de movimento e funcionamento sem JavaScript. Contraste mínimo amostrado do título vermelho: 3,5:1 após correção.
- **Preservação:** HTML institucional com hash SHA-256 original preservado; nenhuma publicação, alteração de produção ou commit realizado.
- **Evidência:** relatórios e capturas em `docs/previews/p2.1-c/` e `docs/previews/hero-opening/`. Testes automatizados em Chromium com viewports simulados e fontes de reserva; aceite visual final realizado pelo responsável em seu navegador.
- **Próxima etapa:** planejar e autorizar P2.2; confirmar o texto institucional da apresentação antes de implementá-lo.

### Checkpoint documental D1.3 — atualização após o aceite da P2.1

- **Data:** 14/10/2026. Atualização documental; sem alterações de código nesta rodada.
- **Estado:** P2.1 permanece aprovada; checklists A–D fechados conforme evidências do checkpoint anterior.
- **Caminhos confirmados:** `cabanas/public/videos/hero.mp4`, `cabanas/public/images/branding/logo RP2.png` e `cabanas/public/images/hero/hero-poster.png`; `cabanas/Hero-1.png` permanece preservado.
- **Prompts 8.1–8.2:** identificados como histórico; o template 8.3 é a referência para waves futuras.
- **Próxima wave:** preparar e autorizar P2.2; definir o texto da apresentação antes de implementar.

### Pendências com momento definido

| Pendência | Resolver em |
|---|---|
| Aprovar texto institucional da apresentação RP2 Cabanas | Planejamento/execução da P2.2 |
| Receber dados e imagens dos dois modelos adicionais | Antes de sua inclusão na P2.3 ou em etapa futura autorizada |
| Aprovar textos, escopos comerciais e preços vigentes | P2.5/P2.6 e revisão final pré-publicação |
| Definir URL, Vercel e link do institucional | P4 |

**Fim do runbook operacional v2.2.**
