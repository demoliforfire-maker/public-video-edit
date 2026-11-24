# Estúdio criativo: como colocar no seu repositório pelo celular

Este zip transforma o seu repositório num estúdio de **posts, carrosséis e edição de vídeo** que você comanda pelo Claude Code do celular. As imagens e os B-rolls são sempre os seus: nada é gerado por IA nem baixado da internet.

## O que vem dentro
- **Posts e carrosséis:** os 5 modelos de criativo do Nexxivo (feed e story), o criativo de story e a animação de 10s que você já tinha, mais um **modelo de carrossel novo** (capa, texto, lista, foto, citação e CTA). Cores, fontes e logo mudam por um arquivo `conteudo.json`. As fontes vão junto, então o render não depende da internet.
- **PhotoCraft** (Photoshop open source, via MCP): trata as suas fotos (máscara, opacidade, curvas, nitidez, lote) antes de entrarem na arte.
- **FilmCraft** (Premiere open source, via MCP): monta o vídeo na timeline, com cortes, B-roll em cima da fala, cor, títulos, legendas e export em MP4.
- **HyperFrames:** vinhetas, lower-thirds e legendas estilizadas.
- **video-use** (opcional): corte automático pela fala. Precisa de uma chave paga da ElevenLabs.
- Regras e skills para o Claude: `estudio/CLAUDE.md`, `post-carrossel` e `editar-video`.

## Passo a passo no celular
1. **Suba o zip para o repositório.** No navegador do celular, abra o repositório no GitHub → **Add file → Upload files** → escolha `estudio-criativo.zip` → **Commit**. O zip tem menos de 25 MB, então passa.
2. **Abra o Claude** → aba **Code** → escolha o repositório → mande:

   > Descompacte o estudio-criativo.zip que está na raiz numa pasta temporária, siga o INSTALAR.md que está dentro dele e, no final, apague o zip do repositório.

3. Ele copia tudo, instala as ferramentas, testa um carrossel de exemplo e pede a sua confirmação para o commit e o PR.

## Ajustes no ambiente da nuvem (uma vez só)
Nas configurações do ambiente do Claude Code (claude.ai/code → ambiente):
- **Rede:** libere o acesso à internet, ou pelo menos estes domínios: github.com, api.github.com, objects.githubusercontent.com, nodejs.org, registry.npmjs.org, cdn.playwright.dev, playwright.download.prss.microsoft.com e playwright.azureedge.net. Sem isso as ferramentas não baixam.
- **Setup script:** `bash estudio/setup.sh`. Assim toda sessão já começa com tudo instalado.
- **Variável de ambiente** (só se for usar o video-use): `ELEVENLABS_API_KEY=...`. Nunca coloque a chave num arquivo do repositório.

## Como pedir depois
- **Carrossel:** suba as fotos para `estudio/posts/projetos/2026-10-20-nome/` e peça: *"Carrossel de 6 telas com essas fotos sobre X. Copy: (o seu texto)."*
- **Post:** *"Modelo 4 no feed com a foto projetos/x/foto.jpg."*
- **Vídeo:** crie `estudio/video/projetos/2026-10-20-nome/` com o `BRIEFING.md` (o modelo está em `estudio/video/`), os brutos em `brutos/` e os B-rolls em `broll/`. Depois peça: *"Leia o BRIEFING.md e edite."*
- As saídas voltam num commit. Baixe pelo app do GitHub.

## Limites
- PhotoCraft e FilmCraft estão em alpha. Se um comando falhar, o Claude usa o ffmpeg ou CSS naquele passo e te avisa.
- GitHub pelo navegador: no máximo 25 MB por arquivo enviado. Para vídeo maior, ponha um link direto de download no briefing.
- A nuvem não tem placa de vídeo, então o render de vídeo é mais lento que no PC.
