# P2.1-C — verificação técnica da Hero

Verificação realizada em 14/10/2026, no build estático local. Estado: verificação técnica concluída; P2.1-D (aceite visual) pendente.

## Resultados

- Astro check: 0 erros, 0 avisos, 0 hints. Build estático aprovado; reconstruído após a correção de contraste.
- Viewports 1440 × 900, 768 × 1024 e 390 × 844: sem overflow horizontal, logo e ações dentro da tela, um único h1.
- Header mantém posição no topo (top = 0) e superfície clara após a rolagem nas três larguras.
- Tab percorre logo, contato do header e contato da Hero; todos têm foco visível com contorno de 3 px. Links do WhatsApp usam o número e mensagem aprovados; nenhuma mensagem foi enviada.
- Vídeo reproduz automaticamente sem áudio, avança e fica visível nas três larguras. Arquivo: MP4, 1280 × 720, 8 s, 6.631.459 bytes (~6,6 MB).
- Movimento reduzido: vídeo sem src, pausado e sem solicitação de rede; poster exibido e rolagem suave desativada.
- Carregamento lento e vídeo bloqueado: poster, texto e ações permanecem disponíveis. Fallback também funciona sem JavaScript.
- Nenhuma exceção JavaScript registrada nos cenários.
- Contraste: mínimo conservador medido para o título vermelho = 3,5:1 (mínimo aplicável a texto grande = 3:1); apoio branco = 15,64:1; texto branco sobre botão vermelho = 5,96:1. Foram amostrados início, meio e fim do vídeo nas três larguras.

## Correção realizada

Reforçada a sobreposição atrás da área do título para corrigir o contraste do vermelho, que inicialmente ficou abaixo de 3:1. A camada preta uniforme continua em 60%; a área de texto no desktop chega a pelo menos 84% até 68% da largura, e tablet/mobile usam aproximadamente 84–86%, além do reforço inferior.

## Limites da verificação

- Testes em Chromium com viewports simulados; sem validação em aparelho físico ou Safari/iOS.
- Google Fonts bloqueado na sessão; a composição foi verificada com Arial Narrow/Arial como fontes de reserva. A configuração de Barlow/Barlow Condensed foi preservada.
- Rede lenta validada para carregamento/fallback; não constitui medição de reprodução em rede móvel real. O original do vídeo foi preservado.
- Estas verificações cobrem os gates solicitados; não são uma auditoria completa de WCAG.

Detalhes automatizados em checks.json e capturas na mesma pasta.
