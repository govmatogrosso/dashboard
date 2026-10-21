# Painel Comunicação Dirigida 2026 · GovMT

Painel publicado no GitHub Pages: **https://govmatogrosso.github.io/dashboard/**
Repositório: https://github.com/govmatogrosso/dashboard

## O que tem nesta pasta

- `index.html`: a página do painel. Não precisa mudar a cada atualização.
- `dados.js`: todos os dados. **Numa atualização normal, só este arquivo muda.**
- `assets/fonts/`: as fontes Boldonse e Google Sans.
- `assets/videos/`: os vídeos e as capas dos Destaques do Mês.
- `.nojekyll`: avisa o GitHub para publicar os arquivos como estão.

## Como atualizar (a cada 15 dias ou uma vez por mês)

### 1. Junte os dados novos

| No painel | Chave no `dados.js` | De onde vem |
|---|---|---|
| Acompanhamento do mês, concluídos por destino e por área | `acompanhamento` | Base do mês no Notion |
| Produção por mês e ranking | `producao` | Planilha de produção (meses já fechados) |
| Stories e ajustes informados à parte | `stories2026`, `ajustes2026` | Informados pela equipe |
| Seguidores | `redes` | Perfis de cada rede |
| Instagram e Facebook | `redes_mensal`, `posts2026` | Exportação de posts da Meta |
| TikTok | `tiktok` | Relatório exportado do TikTok |
| YouTube | `youtube` | YouTube Studio (Shorts) |
| Destaques do Mês | `videos` | Os 3 reels mais vistos do mês, com vídeo e capa em `assets/videos/` |
| Tráfego pago | `trafego` | Gerenciador de anúncios |
| Pautas externas | `pautas` | Planilha de pautas |
| Viagens | `viagens` | Controle de viagens e diárias |

### 2. Atualize as datas no topo do `dados.js`

O começo do arquivo tem um bloco `DADOS_INFO`. É ele que diz ao painel qual é o mês e até quando vai cada exportação:

```js
window.DADOS_INFO = {
  atualizado_em: "2026-11-18",   // dia da atualização (aparece no topo do painel)
  mes_atual: "2026-11",          // mês em andamento: o do acompanhamento do Notion
  ate: {
    tiktok: "2026-11-15",        // último dia do relatório do TikTok
    meta: "2026-11-16",          // último dia da exportação do Instagram e do Facebook
    youtube_inicio: "2023-01-16",// primeiro dia das estatísticas do YouTube
    youtube: "2026-11-16"        // último dia das estatísticas do YouTube
  }
};
```

As datas seguem o formato `ano-mês-dia`. A partir de `mes_atual`, o painel monta sozinho os títulos ("Acompanhamento de novembro"), os meses dos gráficos (de janeiro até o mês atual, que fica marcado com `*`), o cartão do mês no TikTok e os Destaques do Mês.

**Quando o mês vira:** o mês que terminou deixa de vir do Notion e passa a vir da planilha de produção (`producao`). Por isso, ao começar novembro, lance os números finais de outubro na planilha antes de gerar o `dados.js`.

### 3. Gere o `dados.js`

O jeito mais simples é pedir ao Claude. Coloque os arquivos exportados numa pasta, por exemplo `atualizacao-2026-11`, dentro desta pasta. Depois abra o Claude Code nesta pasta e peça: "atualize o painel com os dados desta pasta". O Claude monta o novo `dados.js`, preenche o `DADOS_INFO`, confere os números e publica.

### 4. Publique

Se o Claude não publicou, rode estes comandos no terminal, dentro desta pasta:

```
git add -A
git commit -m "Atualiza dados de novembro"
git push
```

Também dá pelo site: abra o repositório no GitHub e use **Add file → Upload files** para enviar o `dados.js` novo.

Em 1 ou 2 minutos o site atualiza, no mesmo endereço. Para ver a versão nova, aperte Ctrl+F5.

### 5. Confira

Abra o painel e veja se:
- o topo mostra "Dados atualizados em …" com a data certa;
- o título do acompanhamento e o último mês dos gráficos são o mês novo;
- os Destaques do Mês mostram 3 vídeos (se aparecer menos, faltam reels do mês na exportação da Meta).

## Bom saber

- **Virada do ano:** o painel é de 2026. Em janeiro de 2027 é preciso uma versão nova (títulos, filtros de ano e o período eleitoral estão ligados a 2026).
- **Privacidade:** o repositório é público, então qualquer pessoa pode ver os dados do `dados.js`, inclusive nomes da equipe, diárias e pautas.
- **Internet:** a página carrega a biblioteca de gráficos (d3) e, no botão de PDF, a jsPDF de servidores públicos (jsDelivr e cdnjs). Precisa de internet para funcionar.
- **Arquivo antigo:** um `dados.js` antigo, sem `DADOS_INFO`, continua funcionando. O painel usa o último mês da produção e esconde a data de atualização.
