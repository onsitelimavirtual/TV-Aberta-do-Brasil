# TV Aberta Brasil — 1.0

Aplicativo web leve, responsivo, sem bibliotecas externas, com catálogo inicial de **20 emissoras/praças** e acesso às **páginas oficiais** para assistir à TV aberta brasileira quando a emissora disponibiliza sinal na internet. Não é um retransmissor de TV, não inclui IPTV pirata e não promete cobrir todos os canais e municípios do Brasil.

## Como usar
1. **Android, Windows ou Linux:** extraia o arquivo ZIP inteiro e abra `index.html` em um navegador moderno. O catálogo, busca e favoritos funcionam localmente; para assistir, é preciso internet.
2. **Arquivo único:** abra `TV_Aberta_Brasil_Standalone.html`. Não precisa instalar nada para usar o catálogo local. A reprodução continua sendo aberta nas páginas oficiais.
3. **Instalar como app (PWA):** publique a pasta em hospedagem HTTPS (GitHub Pages, Cloudflare Pages etc.) ou execute um servidor em `localhost`. Depois use a opção de instalar/adicionar à tela inicial no navegador, se disponível. O PWA armazena o aplicativo localmente, **não** o vídeo das emissoras.

## Funcionalidades
- Busca sem diferenciar maiúsculas e acentos.
- Filtros por categoria e região, ordenação alfabética e contagem de resultados.
- Salvar/remover favoritos no armazenamento local do navegador.
- Adicionar, remover e salvar links personalizados **do próprio site da emissora**; itens personalizados não são verificados pelo app.
- Importação/exportação de favoritos e canais pessoais para arquivo JSON.
- Tema claro/escuro, layout responsivo, atalhos de teclado nativos em diálogos e alguns recursos de acessibilidade.
- Páginas locais de termos de uso, aviso de privacidade e informação de funcionamento.
- PWA instalável quando servido com HTTPS/localhost (suporte e condições variam de navegador).

## Limites importantes
- **Não é possível garantir todos os canais da TV aberta:** a oferta regional depende da cidade e das autorizações digitais das emissoras.
- O catálogo é um conjunto de links pesquisados, e não um monitor de vídeo ao vivo. A confirmação documental de uma página oficial não equivale a teste de reprodução contínua. A Rede Minas entra como referência institucional, com sinal web não confirmado.
- Alguns serviços exigem cadastro, geolocalização, cookies ou app oficial. Um canal que funciona na antena pode estar indisponível via internet por direitos de exibição.
- Ao acessar um canal, um **novo navegador/aba** abre a página da própria emissora. Não há reprodução hospedada/incorporada no aplicativo.
- O app não registra seus dados em nenhum servidor próprio. Hospedagem pública e sites de destino podem ter regras independentes.
- Compatibilidade com navegadores antigos (por exemplo versões antigas em Windows 7) não está homologada.

## Manutenção do catálogo
Editar `catalog.js`: objetos com `id` único, `name`, `region`, `category`, `url` HTTPS da emissora, `note`, `tone`, `initials`, `access`. Rever URLs, direitos e limitações antes de publicar cada atualização. Alterar também o identificador de cache em `sw.js` para evitar versões antigas. Não adicionar URLs IPTV suspeitas, streams extraídos ou links protegidos por DRM.

## Segurança
HTML de dados personalizáveis é sempre inserido como `textContent` e URLs são aceitas apenas com HTTPS sem credenciais. Isso evita injeção de HTML na interface; não garante que links inseridos pelo usuário sejam legítimos. Para distribuição pública, recomenda-se curadoria editorial e política de retirada de links.

## QA
Execute `node --test tests/catalog.test.cjs`. São testes automatizados do catálogo e validadores, **não** testes reais de vídeo, compatibilidade entre dispositivos ou auditoria jurídica.

## Referências oficiais consultadas em 15/10/2026
- [TV Globo / Globoplay](https://globoplay.globo.com/tv-globo/ao-vivo/7832875/)
- [SBT](https://www.sbt.com.br/ao-vivo)
- [Band](https://www.band.com.br/ao-vivo), [Band Brasília](https://www.band.com.br/ao-vivo/band-brasilia), [Band Vale](https://www.band.com.br/ao-vivo/band-vale)
- [Record](https://record.r7.com/)
- [RedeTV!](https://www.redetv.uol.com.br/aovivo/)
- [TV Cultura](https://cultura.uol.com.br/aovivo/)
- [TV Brasil](https://tvbrasil.ebc.com.br/webtv/)
- [TV Câmara](https://www.camara.leg.br/tv/), [TV Senado](https://www12.senado.leg.br/tv/)
- [TV Justiça / STF](https://portal.stf.jus.br/comunicacao/)
- [Canal Gov](https://canalgov.ebc.com.br/ao-vivo)
- [TV Gazeta](https://www.tvgazeta.com.br/aovivo/)
- [REDEVIDA](https://www.redevida.com.br/ao-vivo/)
- [TV Canção Nova](https://tv.cancaonova.com/TV-AO-VIVO/)
- [TV Aparecida](https://www.a12.com/tv) — emissora veda reprodução de sua transmissão sem autorização
- [TV Novo Tempo](https://www.novotempo.com/)
- [TV Câmara Distrital](https://www.cl.df.gov.br/web/tv-camara-distrital)
- [Rede Minas](https://redeminas.tv/) — verificação institucional apenas, não do sinal online

## Direitos
© 2026 Nailson Rodrigues de Lima (código e identidade visual deste protótipo). Marcas, programação e conteúdo das emissoras pertencem aos seus respectivos titulares. Esta atribuição não presume cessão de direitos sobre materiais de terceiros.
