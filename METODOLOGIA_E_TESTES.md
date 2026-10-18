# Metodologia, cálculos e verificação

## 1. Origem e recorte

O dataset disponibilizado pelo desafio possui **100 linhas** na aba `Sanitized` e **21 colunas**, incluindo campos originais inconsistentes e variantes tratadas. Para a aplicação web, foram usados apenas:

| Campo do HTML | Coluna de origem | Preparação |
|---|---|---|
| `id` | `sale_id` | Identificador inteiro; 100 IDs distintos. |
| `date` | `SaleDateSanitized` | Datas ISO mantidas; `INVALID` convertido a `null`. |
| `model` | `PorscheModelSanitized` | Descrição normalizada do modelo. |
| `year` | `ModelYearSanitized` | Ano do modelo numérico; **não** ano da venda. |
| `price` | `SalesPriceSanitized` | Preço numérico em USD, mantendo centavos. |
| `payment` | `PayMethodSanitized` | Categoria de pagamento já normalizada. |
| `city` | `CitySanitized` | Cidade normalizada. |
| `state` | `StateSanitized` | Sigla do estado normalizada. |
| `status` | `DeliveryStatusSanitized` | Status normalizado, preservado em sua forma original. |

`customer_name`, `salesperson`, campos originais de texto e quilometragem **não foram publicados** no HTML nem no CSV derivado. Isso minimiza divulgação de dados pessoais e de campos sem relação com as perguntas de negócio.

## 2. Regras de cálculo

Todos os cálculos são refeitos **no navegador** em cada mudança de filtro, sobre o conjunto de registros selecionado `S`:

- **Valor total registrado:** `sum(price)` para todos os registros de `S`, inclusive cancelados.
- **Valor não cancelado:** `sum(price)` apenas para status diferente de `Cancelled`. Não equivale a receita recebida/contabilizada.
- **Registros:** número de linhas de `S`.
- **Valor médio:** total registrado ÷ registros; em seleção vazia é exibido zero.
- **Percentual entregue:** registros com status `Delivered` ÷ total de registros.
- **Datas inválidas:** linhas em que o campo sanitizado originalmente dizia `INVALID` (armazenadas como `null`).
- **Ranking de modelos:** agrupamento pela categoria `model`, agregação por soma de valores ou quantidade e ordenação decrescente; são exibidos os oito líderes do recorte.
- **Ranking de estados:** agrupamento por `state`, soma de `price`, oito líderes em ordem decrescente.
- **Pagamentos:** soma de `price` agrupada por `payment`, sem presumir liquidação.
- **Situação operacional:** `Delivered`, `Cancelled` e todos os demais status agrupados como “Outros status” (não necessariamente pendentes).
- **Participação do líder:** métrica do líder ÷ soma da mesma métrica no conjunto filtrado.

Filtros por modelo, cidade, ano do modelo, pagamento, estado, status e busca textual são **combinados por interseção**. A exportação CSV inclui exatamente as linhas do resultado atual, com campos sanitizados e sem nomes pessoais.

## 3. Números de controle na base completa

| Indicador | Esperado |
|---|---:|
| Total de linhas | 100 |
| IDs únicos | 100 |
| Modelos distintos | 40 |
| Estados distintos | 33 |
| Valor total | USD 12,827,800.50 |
| Valor não cancelado | USD 12,202,550.50 |
| Valor cancelado (7 registros) | USD 625,250.00 |
| Entregues | 41 |
| Outras situações (não entregues nem canceladas) | 52 |
| Datas válidas | 76 |
| Datas inválidas | 24 |
| Período das datas válidas | 2024-03-14 a 2027-10-01 |

Para o subconjunto com `state = CA`, existem **16 registros**, totalizando **USD 1,973,350.00**. Ao acrescentar `year = 2024` (ano do **modelo**), restam **7 registros**, totalizando **USD 1,029,000.00**.

## 4. Testes realizados no navegador

A versão do `index.html` entregue foi aberta e exercitada no **Chromium**, com JavaScript ativo, incluindo verificação de erros de execução:

- Renderização inicial: 100 registros, total USD 12,827,800.50; KPIs e gráficos presentes; **nenhum erro de JavaScript**.
- Seleção do estado CA: 16 registros, total USD 1,973,350.00.
- CA + ano do modelo 2024: 7 registros, total USD 1,029,000.00.
- Clique na barra do modelo líder: aplica seleção do modelo em todas as seções.
- Busca sem correspondência: exibe zeros e estados vazios sem falha.
- Visualização móvel com largura de 390 px: sem estouro da largura horizontal.
- Capturas registradas em `dashboard_visao_geral.png`, `dashboard_filtro_aplicado.png` e `dashboard_mobile.png`.

**Limite do teste:** a aplicação foi validada no navegador local; a URL pública do GitHub Pages deve ser testada **depois** da publicação. O dashboard não consulta servidores e pode ser aberto como um único documento HTML.

## 5. Restrições e interpretações

- A amostra é educacional, sem pretensão de representar vendas oficiais da Porsche.
- A origem mistura registros com datas de 2024 a 2027; o dashboard **não** afirma que esses períodos ocorreram no mundo real.
- 24 datas são inválidas; foram excluídas de qualquer análise temporal potencial, mas permanecem nos KPIs por modelo, estado e pagamento.
- A condição `Delivered` não prova recebimento; `Cancelled` é excluída apenas do valor não cancelado.
- Os rótulos USD refletem a denominação das entradas da origem; não há conversão de moeda.
- Categorias de meios de pagamento (por exemplo, `Wire Transfer` e `Bank Transfer`) foram preservadas como categorias distintas porque assim estão na base sanitizada.
- Filtros alteram o denominador: participação de liderança deve ser lida sempre **no recorte exibido**.

## 6. Atualização da base

O projeto é propositalmente um arquivo HTML único, com a constante JavaScript `DATA` embutida. Para usar uma nova versão da base, mantenha os nomes de campos e os tipos da seção 1 e substitua essa coleção no `index.html` (ou automatize essa substituição com um script local). Execute novamente os testes do bloco 4. O arquivo `dados_sanitizados.csv` documenta o formato, mas não é lido automaticamente pelo HTML publicado.
