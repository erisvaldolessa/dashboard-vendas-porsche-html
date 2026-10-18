# Entrega do desafio na DIO

## Link do repositório

https://github.com/erisvaldolessa/dashboard-vendas-porsche-html

## Link do dashboard (depois de habilitar o Pages)

https://erisvaldolessa.github.io/dashboard-vendas-porsche-html/

*Este é o endereço esperado quando o repositório é publicado com esse nome; confirme que a página abre antes de submeter.*

## Descrição pronta para colar no formulário

Desenvolvi um dashboard de vendas da Porsche em HTML, CSS e JavaScript, partindo de uma planilha educacional sanitizada com 100 registros. O painel foi estruturado para responder a três perguntas de negócio: quais modelos concentram mais valor, em quais estados se distribuem os registros e como se comportam os meios de pagamento e os status de entrega.

A aplicação possui filtros combináveis por modelo, cidade, ano do modelo, pagamento, estado e status, além de indicadores de valor registrado, valor não cancelado, quantidade, valor médio, entregas e qualidade de dados. Também inclui busca, tabela detalhada e exportação CSV dos registros filtrados.

Durante o tratamento, preservei as informações normalizadas da base, removi campos pessoais desnecessários e sinalizei 24 datas inválidas e sete registros cancelados, evitando interpretar valores registrados como receita efetivamente recebida.

O projeto foi produzido em um único arquivo `index.html`, sem dependências externas, com layout responsivo e dados embutidos. O repositório contém a aplicação, o extrato sanitizado, capturas de tela, metodologia, testes, especificação do prompt e instruções para publicação no GitHub Pages.

Dashboard publicado (verificar antes de enviar): https://erisvaldolessa.github.io/dashboard-vendas-porsche-html/

## Teste rápido de publicação

Após habilitar o GitHub Pages, aplicar `Estado = CA` e `Ano do modelo = 2024` deve mostrar **7 registros** e **US$ 1.029.000,00**. Sem filtros, a base deve mostrar **100 registros** e **US$ 12.827.800,50**.
