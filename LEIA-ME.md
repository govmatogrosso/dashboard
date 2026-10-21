# Painel Comunicação Dirigida 2026 · GovMT

Versão independente do painel, pronta para o GitHub Pages. Abre em qualquer navegador, sem login.

## O que tem nesta pasta

- `index.html`: a página do painel.
- `dados.js`: todos os dados (redes, produção, acompanhamento, ranking, pautas, viagens, tráfego). Para atualizar números, é este arquivo que muda.
- `assets/fonts/`: as fontes Boldonse e Google Sans.
- `assets/videos/`: os vídeos e as capas dos Destaques do Mês.
- `.nojekyll`: avisa o GitHub para publicar os arquivos como estão.

## Como publicar no GitHub Pages

1. Entre em github.com e crie uma conta gratuita (ou use a sua).
2. Clique em **New repository**. Dê um nome, por exemplo `painel-govmt`, marque **Public** e clique em **Create repository**.
3. Na página do repositório, clique em **uploading an existing file** (ou **Add file → Upload files**).
4. Arraste para a página **o conteúdo desta pasta**: `index.html`, `dados.js` e a pasta `assets` inteira. Clique em **Commit changes**.
5. Vá em **Settings → Pages**. Em **Branch**, escolha `main` e a pasta `/ (root)`, e clique em **Save**.
6. Em um ou dois minutos o painel estará no ar em `https://SEU-USUARIO.github.io/painel-govmt/`.

## Como atualizar

Peça ao Claude uma nova versão e substitua os arquivos que mudaram (normalmente só `dados.js`, às vezes `index.html`) com **Add file → Upload files**. O endereço continua o mesmo.

## Bom saber

- O repositório público deixa os arquivos visíveis para qualquer pessoa, inclusive os dados de `dados.js` (nomes da equipe, diárias, pautas).
- A página carrega a biblioteca de gráficos (d3) e, no botão de PDF, a jsPDF de servidores públicos (jsDelivr e cdnjs). Precisa de internet para funcionar.
- O acompanhamento de outubro é uma cópia do Notion do dia da geração. Ele não se atualiza sozinho.
