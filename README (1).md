# Painel de Cobertura de SKUs

Painel de positivação de mix por cliente — Backoffice Comercial, linha de congelados.

**Acesso:** https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/

## O que ele mostra

Base de faturamento por representante, com os clientes classificados pela quantidade de
SKUs distintos comprados no período. A meta é **3 SKUs distintos por cliente**.

- **3 SKUs ou mais** — meta atingida
- **2 SKUs** — falta 1 item
- **1 SKU** — mix baixo

## Como usar

1. Selecione o vendedor no topo.
2. Filtre pela faixa de mix ou busque um cliente pelo nome/código.
3. Clique no cliente para ver quais produtos ele já compra.
4. **Enviar no WhatsApp** — gera a imagem com os clientes de 1 e 2 SKUs e abre a conversa
   com a mensagem pronta. No celular a imagem vai anexada automaticamente; no computador
   ela é copiada, basta colar com `Ctrl + V` na conversa.
5. **Baixar Excel** — planilha `.xlsx` com duas abas (resumo por cliente e detalhe por
   produto), somente com os clientes de 1 e 2 SKUs.

## Estrutura

Arquivo único, sem build e sem servidor. Os dados ficam embutidos no próprio `index.html`.

| Arquivo | Conteúdo |
| --- | --- |
| `index.html` | Painel completo: layout, lógica e dados do período |

## Atualizar o período

Os dados vivem em uma constante `DADOS` no fim do `index.html`, no formato:

```js
{
  periodo: "Setembro/2026",
  grupos:  ["BATATAS", "..."],        // categorias
  produtos:["BATATA PALITO...", "..."],// SKUs
  pg:      [0, 0, 1, ...],             // grupo de cada SKU, por índice
  reps:    [ ["NOME DO REPRESENTANTE", [ ["01-000000","CLIENTE",2,[3,17]] ]] ]
}
```

Cada cliente é `[código, nome, qtde de SKUs, índices dos produtos]`. Para trocar o mês,
gere esse bloco a partir do export do BI e substitua a constante.
