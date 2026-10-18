# Publicação no GitHub e ativação do GitHub Pages

## 1. Criar repositório

1. Entre em https://github.com/new com sua conta.
2. Repositório sugerido: **`dashboard-vendas-porsche-html`**.
3. Descrição sugerida: `Dashboard interativo de vendas Porsche em HTML, com KPIs, filtros, análises de modelos, estados, pagamentos e qualidade dos dados. Projeto educacional DIO.`
4. Selecione **Public**.
5. Deixe **Add README = Off**, **No .gitignore** e **No license**: os arquivos necessários já estão incluídos.
6. Clique em **Create repository**.

## 2. Carregar o projeto

1. Na página do novo repositório, clique em **uploading an existing file**.
2. Extraia o ZIP fornecido e entre **na pasta extraída**.
3. Selecione todos os arquivos da pasta (**não** selecione o ZIP fechado nem uma pasta pai).
4. Arraste todos os arquivos para a área de upload. Confirme se `index.html`, `README.md` e as imagens aparecem **na raiz** do repositório.
5. Mensagem de commit sugerida: `Publica dashboard interativo de vendas Porsche`.
6. Clique em **Commit changes**.

## 3. Habilitar o GitHub Pages

1. Dentro do repositório, clique em **Settings**.
2. No menu lateral, escolha **Pages**.
3. Em **Build and deployment → Source**, selecione **Deploy from a branch**.
4. Em **Branch**, escolha **main** e **/(root)** e clique em **Save**.
5. Aguarde a publicação e atualize a página de Settings → Pages. Se o nome sugerido foi usado, a URL esperada é:
   
   **https://erisvaldolessa.github.io/dashboard-vendas-porsche-html/**

O domínio acima é o **endereço esperado**, não uma confirmação de que a página já foi publicada. Se o nome do repositório for outro, ajuste a URL.

## 4. Conferência obrigatória antes da DIO

- Acesse a URL pública do Pages em uma aba anônima (não apenas o `github.com/...`).
- Confira a seção de KPIs: **100 registros** e **US$ 12.827.800,50** antes de aplicar filtros.
- Filtre **Estado = CA** e **Ano do modelo = 2024**: devem restar **7 registros** e **US$ 1.029.000,00**.
- Confirme que os gráficos mudam com os filtros e que o botão de limpar restaura 100 registros.
- Verifique se as imagens aparecem no `README.md` e se o botão de exportação CSV funciona.
- Confira que o repositório é **Public**.

## 5. Entregar na DIO

Na área do desafio, utilize como link de repositório:

`https://github.com/erisvaldolessa/dashboard-vendas-porsche-html`

No campo descrição, copie o texto de [`ENTREGA_DIO.md`](ENTREGA_DIO.md) e inclua, se houver espaço, a URL **já publicada** do GitHub Pages.

**Aviso:** no GitHub, o endereço `/blob/main/index.html` mostra código, não o dashboard funcionando. O link do dashboard deve ser o do GitHub Pages, terminado em `/dashboard-vendas-porsche-html/`.
