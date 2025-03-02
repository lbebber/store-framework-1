# Carrossel de blocos

## :sparkles: **Branch:** slider

## Introdução

O Slider Layout, como o Flex Layout, é uma forma flexível de criar um novo bloco a partir de outros blocos usando `children`. Ele permite que sejam criados sliders de outros blocos, como `info-card`s e até mesmo `flex-layout`s por exemplo.

Vamos utilizar o Slider Layout para tornar um conjunto de info-cards em um slider.

## Slider Layout

Analisando a [documentação](https://vtex.io/docs/components/layout/vtex.slider-layout), vemos que você pode utilizar qualquer _array_ de blocos como `children`, assim como no Flex Layout.

Abaixo, segue um exemplo de implementação de um slider-layout com dois `info-card`s na home:

```json
{
  "store.home": {
    "blocks": ["slider-layout#home"]
  },
  "slider-layout#home": {
    "children": ["info-card#1", "info-card#2"],
    "props": {
      "autoplay": {
        "timeout": 5000,
        "stopOnHover": false
      }
    }
  },
  "info-card#1": {
    "props": {
      "imageUrl": "https://images.unsplash.com/photo-1524185962737-ea7c028a12cd?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80",
      "isFullModeStyle": true,
      "headline": "Black Friday",
      "callToActionText": "Subscribe",
      "textPosition": "center"
    }
  },
  "info-card#2": {
    "props": {
      "imageUrl": "https://images.unsplash.com/photo-1524185962737-ea7c028a12cd?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80",
      "isFullModeStyle": true,
      "headline": "Black Friday",
      "callToActionText": "Subscribe",
      "textPosition": "center"
    }
  }
}
```

## Tarefa

Nesta tarefa, vamos criar um slider de marcas para o nosso site:

![](https://appliancetheme.vteximg.com.br/arquivos/brand-slider.png)

1. Crie um arquivo chamado `slider-layout#home.jsonc`
2. Acrescente o bloco `slider-layout#home` ao `store.home`
3. Neste arquivo, baseando-se no código acima, apague os `info-card` declarados para o bloco `slider-layout#home` e adicione 6 componentes `image` como children. Utilize o formato `image#brand1`, `image#brand2` e etc para declarar os componentes.
4. Declare uma prop `src` específica para cada `image#brand`. Utilize as URLs abaixo para cada uma delas:
   1.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square1.png`
   2.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square2.png`
   3.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square3.png`
   4.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square4.png`
   5.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square5.png`
   6.  `https://appliancetheme.vteximg.com.br/arquivos/flatflat-brand-logo-square6.png`
5. Por fim, você pode utilizar a propriedade de `autoplay` no bloco `slider-layout#home`. Faça com que o slide aconteça automaticamente a cada 7 segundos e que ele pare quando o usuário passar o mouse em cima do slide.