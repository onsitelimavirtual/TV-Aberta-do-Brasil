# Registro de QA — TV Aberta Brasil 1.0
Data da revisão documental: 15/10/2026.

## Passagem A — interpretação e aderência
- Objetivo original: criar aplicativo com canais de TV aberta gratuitamente disponíveis. **Atendido parcialmente:** guia funcional para páginas oficiais; ainda não há cobertura universal nem player integrado.
- Limite técnico-jurídico: sinal de TV aberta por antena não significa direito de retransmissão via software. Conteúdo de terceiros não é copiado, gravado, extraído nem re-hospedado.
- Catálogo inicial: 20 entradas de canais/praças. Rede Minas incluída como consulta institucional com transmissão web não confirmada.
- Produto concebido como app HTML/CSS/JavaScript responsivo sem serviço pago de backend.

## Passagem B — resultados observados
- `node --check app.js`, `node --check catalog.js`, `node --check sw.js`: **APROVADO** (sintaxe).
- `node --test tests/catalog.test.cjs`: **5 de 5 testes aprovados**.
  1. Integridade de 20 entradas, IDs sem repetição, URLs válidas e campos necessários: aprovado.
  2. Endereços não duplicados e contagem de destaques: aprovado.
  3. Bloqueio de protocolos não HTTPS/URLs com credenciais: aprovado.
  4. Busca sem distinção de acentos/maiúsculas: teste da função de normalização aprovado.
  5. Categorias de catálogo previstas: aprovado.
- Pesquisa das páginas oficiais por fontes online: **realizada documentalmente**. Não constitui teste de player, de vídeo, de desempenho dos servidores das emissoras ou de disponibilidade 24 horas.
- Tentativa de teste funcional no Chromium do ambiente com arquivo local e servidor de teste localhost: **BLOQUEADA PELO AMBIENTE**, erro `net::ERR_BLOCKED_BY_ADMINISTRATOR`. Não há evidência para afirmar teste visual aprovado.

## Roteiro de aceite manual ainda pendente
| ID | Passo | Resultado esperado | Status |
|---|---|---|---|
| UI-01 | Abrir `index.html` no navegador Android atual | Renderização responsiva, 20 canais sem corte horizontal | PENDENTE |
| UI-02 | Abrir em desktop atual | 4 colunas e menus navegáveis | PENDENTE |
| UI-03 | Pesquisar "Canção" | Filtra TV Canção Nova | PENDENTE |
| UI-04 | Escolher categoria Pública e legislativa | Mostra canais da categoria | PENDENTE |
| UI-05 | Favoritar o SBT e atualizar página | Favorito mantém-se, se armazenamento permitir | PENDENTE |
| UI-06 | Abrir SBT no portal oficial | Nova aba abre endereço HTTPS da emissora | PENDENTE |
| UI-07 | Cadastrar canal de URL HTTPS, exportar e importar | Restauração dos itens personalizados | PENDENTE |
| UI-08 | Inserir URL javascript: ou HTTP | Cadastro é rejeitado | PENDENTE |
| UI-09 | Desligar internet após primeiro acesso | Interface em cache em implantação PWA; links de vídeo sem sinal | PENDENTE |
| UI-10 | Validar com leitor de tela e teclado | Foco visível, diálogos acessíveis | PENDENTE |
| LIVE-01 | Verificar cada emissora no local do usuário | Confirmar reprodução, cadastro e restrições regionais | PENDENTE |
| LEGAL-01 | Revisar termos, marca e política de privacidade antes da distribuição | Homologação jurídica/editorial | PENDENTE |

## Riscos residuais
- Streaming e links externos podem mudar, sair do ar ou exigir contas e geolocalização.
- Não existe compromisso de cobertura de toda emissora ou município.
- Instalação PWA depende de navegador moderno, HTTPS/localhost e políticas do dispositivo.
- Marcadores de fontes oficiais referem-se aos domínios do catálogo, não a um monitoramento de segurança em tempo real.
- A política jurídica é uma minuta técnica; exige análise final para fins de comercialização/distribuição ampla.

**Status:** protótipo funcional implementado com testes estáticos e unitários aprovados, **não homologado** em campo.
