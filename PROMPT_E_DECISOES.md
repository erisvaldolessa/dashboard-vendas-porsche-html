# Prompt de especificação e decisões de refinamento

## O que foi solicitado no desafio

Construir a partir da planilha sanitizada da Porsche um **dashboard HTML de arquivo único**, publicado no GitHub Pages, com ao menos três perguntas de negócio, filtros adequados, KPIs e identidade visual coerente. Documentar o prompt e o que mudou entre a concepção e a entrega.

## Especificação consolidada do dashboard

O texto abaixo é uma **síntese da especificação técnica de construção**, não uma transcrição literal de um único prompt histórico:

> Crie uma aplicação web de painel de vendas Porsche em **um único `index.html`**, sem bibliotecas externas, a partir de 100 registros da planilha sanitizada. Exclua campos de nomes pessoais. Responda a três perguntas de negócio: quais modelos lideram por valor e quantidade, onde se concentram os registros por estado e como se distribuem os pagamentos e as situações de entrega. Inclua filtros combináveis por modelo, cidade, ano do modelo, pagamento, estado e status, além de KPIs atualizados, busca, tabela paginada e exportação CSV. Use uma linguagem visual elegante, responsiva e acessível, com referência cromática vermelho, preto e cinza. Diferencie valor registrado e valor não cancelado; mostre 24 datas inválidas e sete cancelamentos sem inventar valores ausentes. Produza documentação, capturas da tela e um repositório pronto para GitHub Pages.

## Mudanças entre o briefing e a solução final

| Aspecto | Briefing | Decisão implementada e justificativa |
|---|---|---|
| Gráficos | No mínimo três perguntas | Três seções narrativas com rankings de modelos e estados, pagamento e entrega; as perguntas são explícitas na interface. |
| Filtros | Modelo, cidade, ano e pagamento | Incluídos também estado, status e busca por ID/modelo/cidade para fazer cruzamentos úteis. |
| Valores | Receita e vendas | Dois valores separados: total registrado e total não cancelado; não tratar cancelamentos ou pendências como caixa recebido. |
| Qualidade | Base sanitizada | Evidência quantitativa de 24 datas inválidas; dados não foram corrigidos por hipótese. |
| Privacidade | Dados da planilha | HTML e CSV incluem somente nove campos necessários, sem nomes de clientes ou vendedores. |
| Evidência | Publicação com filtro | Imagens de visualização inicial, de filtros CA + 2024 e de layout móvel. |
| Infraestrutura | Página web com URL própria | Arquivo autônomo `index.html`, sem CDN nem servidor de dados, compatível com GitHub Pages. |

## Por que essas três perguntas?

**Modelos** conectam o painel a decisões de portfólio e permitem distinguir quantidade de registros de valor. **Estados** localizam concentração geográfica na amostra e possibilitam detalhar cidades. **Pagamentos e status** oferecem visão do mix de transações e evitam interpretar o total registrado como receita líquida.

O propósito é apoiar a leitura crítica dos dados, não sugerir causalidade ou extrapolar a amostra para o mercado automotivo.

## Processo de verificação

A construção foi seguida por verificação no Chromium dos totais, dos filtros combinados e do layout responsivo. Os casos objetivos e seus resultados estão em [METODOLOGIA_E_TESTES.md](METODOLOGIA_E_TESTES.md). O endereço definitivo do GitHub Pages deverá ser verificado após o deploy.
