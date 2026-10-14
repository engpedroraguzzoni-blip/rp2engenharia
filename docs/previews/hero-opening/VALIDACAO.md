# Abertura suave — validação

Implementação em CSS, concluída em 14/10/2026. Cabeçalho: fade de 400 ms. Identificador: atraso de 100 ms e duração de 550 ms; título: 160/650 ms; apoio: 300/550 ms; botão: 420/500 ms. Sequência termina em 920 ms. Conteúdo da Hero percorre 12 px para cima.

Check e build aprovados, sem erros ou avisos. Testes em 1440 × 900, 768 × 1024 e 390 × 844 confirmaram layout estável, ausência de overflow, estado final totalmente visível, header fixo no topo, foco visível, revelação imediata ao receber foco e hover separado da entrada. O foco não reinicia a sequência.

Movimento reduzido, antes do carregamento e durante a entrada, deixa o conteúdo visível sem deslocamento. Carregamento lento, falha do vídeo e JavaScript desativado permitem que a abertura termine normalmente. Nenhuma exceção JavaScript registrada. Nenhum novo JavaScript, biblioteca ou dependência foi adicionado ao produto.

Capturas dos estágios 0, 200, 600 e 1000 ms e das três larguras estão nesta pasta. Os estágios foram inspecionados usando o relógio das animações do navegador. Dados detalhados em checks.json.

Limites: Chromium com viewports simulados e fontes de reserva; sem aparelho físico/Safari nesta rodada. A avaliação visual final deve ser feita na prévia local, recarregando a página.
