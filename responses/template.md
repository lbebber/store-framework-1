# Criando templates customizados

## :sparkles: **Branch:** template

## Introdução

Lojas são compostas por várias páginas diferentes, cada uma com layout e conteúdo específicos. Ao criar uma loja do zero no VTEX IO, algumas páginas padrão com URLs predefinidas já são disponibilizadas para você. Abaixo, vemos uma lista com algumas dessas páginas padrão:

- `store.home` (Home page)
- `store.product` (Product page)
- `store.search` (Search Results page)
- `store.account` (Client Account page)
- `store.login` (Login page)
- `store.orderplaced` (Order Placed page)

Mas é possível que você queira criar uma landing page customizada. Nesse caso, você deve criar uma nova URL e um conteúdo específico para exibir aos usuários que acessarem essa rota.

## Criando uma Landing Page

São necessários poucos passos para se criar uma landing page customizada:

1. Criar um novo template no tema sua loja
2. Criar o novo path para acessar este template

### Template

Um template define o layout da página. Portanto, se você deseja criar uma página personalizada, também precisará criar um novo template no seu tema.

Vamos supor que você queira criar uma página simples com informações sobre a sua loja. Dentro da pasta `blocks`, você pode criar um arquivo que contenha o seguinte código, declarando um novo template para uma página customizada,

```json
{
 "store.custom#{templatename}": {
     "blocks": [
     ]
  }
}
```
onde `{templateName}` deve ser substituído pelo nome identificador do template.

A seguir, você deve preencher o código com os componentes necessários para montar o layout. Abaixo, vemos um exemplo dessa implementação:

```json
{
 "store.custom#{templatename}": {
   "blocks": [
     "flex-layout.row#about-us"
   ]
 },
 "flex-layout.row#about-us": {
   "children": [
     "image#about-us",
     "flex-layout.col#text-about-us"
   ]
 },
 "flex-layout.col#text-about-us": {
   "children": [
     "rich-text#about-title",
     "rich-text#about-content"
   ],
       "props": {
     "preventVerticalStretch": true
   }
 },
"rich-text#about-title": {
   "props": {
     "text":
     "# About us Title"
   }
 },
 "rich-text#about-content": {
   "props": {
     "text":
     " About us content - Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum"
   }
 },
 "image#about-us": {
   "props": {
     "src": "https://storecomponents.vteximg.com/files/mobile-phone.png",
     "maxHeight": "600px"
   }
 }
}
```

### Path

Agora que um novo template com o layout da página foi definido no código do tema da loja, a próxima etapa é definir o caminho (path) da página que acessará este layout.

Devemos criar um arquivo `routes.json` dentro da pasta `store` do seu tema. Após isto, insira o código abaixo,

```json
{
  "store.custom#about-us": {
    "path": "/{URL}"
  }
}
```

onde `{URL}` é o nome do caminho desejado

## Tarefa

Vamos criar uma página com informações sobre a sua loja conforme o exemplo abaixo:

![](https://user-images.githubusercontent.com/12139385/63775975-dbdfef80-c8b6-11e9-9b76-e50924b828ae.png)

1. Na pasta `blocks`, crie um arquivo `about-us.jsonc`
2. Declare um template `store.custom#about-us` neste arquivo
3. Inclua um block "flex-layout.row#about-us" neste template
4. Após declarar o flex-layout.row, utilize o código do exemplo dado acima para completar o layout da página
5. Na pasta `store`, crie um arquivo `routes.json`
6. Neste arquivo, declare um path `/about-us`
7. Com o código linkado, acesse `{workspace}--appliancetheme.myvtex.com/about-us` para ver sua nova landing page