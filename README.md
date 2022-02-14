# Responsividade

- O que é responsividade?
- O que é um site responsivo?
- Quais vantagens?
- Como deixar um site responsivo?
  - Media Queries
  - Breakpoints
- Mobile first
- Porque usar mobile first?
- Flex e grid
- Páginas não responsivas
- Páginas responsivas

### O que é responsividade?

Antigamente, ao construir o layout/design de um website era relativamente mais simples, pois a variação de tamanho de monitores era muito limitada. Eu inclusive me lembro q era comum que todo mundo tivesse as mesmo tamanhos de monitor e era raro ves alguem com um monitor maior.

Assim, ao criar o layout de uma site, não era tão desafiador pois o acesso a internet era restrito a computadores que em sua maioria teriam os memos tamanho de monitor ou monitores de tamanhos muito semelhantes. Inclusive, se você acessar um site antigo, você pode se deparar com um website que só atendia a um tamanho de monitor, geralmente 1024px. Se seu monitor fosse maior ou menor, vc teria um scroll na pagina ou uma parte em branco.

Com advento de smartphones, tables e afins, surgiu a necessidade de de adaptar o layout do website em telas de tamanhos diferente. No começo e ainda hoje, empresas criam 2 layout, um para desktop e outro para dispositivos mobile. Com isso, ao entrar em algum site desse tipo, você seria redirecionado para página mobile caso estivesse em um dispositivo movel.

Por exemplo:

- www.facebook.com -> desktop
- www.m.facebook.com -> mobile, sim eles adicionam o `.m` na frente da url

Mas hoje em dia isso não é mais necessario devido a responsividade. Em poucas palavras, responsividade é uma maneira de adaptar o layout de acordo com o tamanho da tela do usuário.

### O que é um site responsivo?

Com isso, um site responsivo seria um site aonde o conteúdo irá se adaptar de acordo com o sua tela.

Um exemplo, imagina q você esteja construindo um site que vai mostrar suas fotos como se tivesse em uma tabela:

|----------------------------------------------------------------|
|                                                                |
|   |----------------|  |----------------|  |----------------|   |
|   |                |  |                |  |                |   |
|   |    Foto 1      |  |      Foto 2    |  |     Foto 3     |   |
|   |                |  |                |  |                |   |
|   |                |  |                |  |                |   |
|   |----------------|  |----------------|  |----------------|   |
|                                                                |
|----------------------------------------------------------------|

Você poderia escolher quantas colunas você mostraria de acordo com o tamanho da tela.
- Em desktop -> 3 fotos por linha
- Em table   -> 2 fotos por linha
- Em mobile  -> 1 fotos por linha

Isso tudo pode ser feito somente com HTML e CSS.

Com isso, você não precisará ter mais de 1 versão do seu site para cada dispositivo e seu site não precisa saber se o usuário está acessando de um computar de mesa, notebook, celular, ou qualquer dispositivo. Pois o mesmo irá adaptar seu conteúdo de acordo com o tamanho da tela.

### Quais vantagens?

Como já dito anteriormente, uma das vantagens é ter somente uma versão do seu site que irá se adaptar, em vez de ter 2 ou mais versão para manutenção.

Isso também ajudará a caso precise substituir alguma parte do seu site. Hoje o conceito de componentização é mais comun, aonde seu site é construido usitlizando componentes, se esse componentes forem responsivos você não terá tanta dor de cabeça na mora de fazer qualquer coisa no seu site.

Consequentimente, isso ajudará na interação do usuário no seu site. Um site responsivo consegue segurar o usuário por mais tempo e proporcionar sempre a melhor experiência possível em todos os tipos de tela.

Ajuda no SEO da sua página

> O Search Engine Optimization ou SEO é o conjunto de técnicas que um profissional de marketing pode implementar, visando alcançar melhores resultados para o seu site ou artigo nos mecanismos de busca, como o Google.

Ou seja, mecanismos de busca como o Google avaliam seu site antes de mostar o link para o mesmo. Quanto melhor o site, melhores as chances de ficar em primeiro e responsividade é um dos pontos considerados para rankear seu site.

### Como deixar um site responsivo?

Bem, você já deve estar se perguntando como deixar seu site responsivo. Acredito que o principal seria o uso de [Media Queries](https://developer.mozilla.org/pt-BR/docs/Web/CSS/Media_Queries/Using_media_queries).

#### Media Queries

Media Queries é uma técnica que permite mudar seus estilos CSS para diferentes resoluções, deixando seu site responsivo.

Basicamente, permite criar condições no seu CSS para que determinado estilo seja aplicado quando satisfazer determinadas condições. Você pode aplicar várias condições na sua media query, mas vou falar da principal que é condição de tamanho de tela.

Dado seguinte exemplo:
```css
.my-app {
  display: block;
  background-color: red;
  font-size: 18px;
}

@media (min-width: 600px) {
  .my-app {
    background-color: blue;
  }
}
```
Neste exemplo, eu crio uma classe chamada `.my-app`, aonde eu aplico um `display`, `background-color` e uma `font-size`. Ao declara essa media query especificada através do `@media`, eu estou dizendo o seguinte:
> Quando a tela possiur pelo menos `600px` de largura (`width`), aplique esses estilos.

Ou seja, se sua tela for menor que `600px` ela ficará na cor vermelha (`red`), caso contrário será azul (`blue`).

Como eu só especifiquei o `background-color` na media query, as outras propriedades não mudarão.

#### Breakpoints

Com o surgimento de media queries, logo surgiram o Breakpoints que são pontos de quebra de layout. Me lembro que o [Bootstrap](https://getbootstrap.com/) implementou isso e logo se tornou um famoso freamework de CSS.

O mesmo define o seguintes breakpoints:

| Nome              | Breakpoint | Tamanho da tela    |
|-------------------|------------|--------------------|
| X-Small           | xs         | 0px até 575px      |
| Small             | sm         | 576px até 767px    |
| Medium            | md         | 768px até 991px    |
| Large             | lg         | 992px até 1199px   |
| Extra large       | xl         | 1200px até 1399px  |
| Extra extra large | xxl        | 1400px ou mais     |

[Mais detalhes aqui](https://getbootstrap.com/docs/5.1/layout/breakpoints/)

Com isso, você pode contar com essas medias queries declarando seu CSS assim:
```css
@include media-breakpoint-up(sm) { /* CSS aplicado em telas de 576px até 767px */ }
@include media-breakpoint-up(md) { /* CSS aplicado em telas de 768px até 991px */ }
@include media-breakpoint-up(lg) { /* CSS aplicado em telas de 992px até 1199px */ }
@include media-breakpoint-up(xl) { /* CSS aplicado em telas de 1200px até 1399px */ }
@include media-breakpoint-up(xxl) { /* CSS aplicado em telas de 1400px ou mais */ }
```

Importante, o tamanho `xs` possui ão possui um breakpoint pois deve-se utilizar da estratégia _mobile first_ que falaremos na sequência.

Esses breakpoint permitem estilizar mais facilmente seu site, por exemplo, os breakpoints `xs` e `sm` vão ser utilizado em celulares devido tamanho de tela, `md` em tablets, `lg` em desktops, `xl` em desktops com tela grande e `xxl` em desktops ainda maiores.

### Mobile first

Em poucas paravras, _mobile first_ é criar seu site pensando em diposivitos mobiles (pequenos) e depois adaptar para dispositivos desktops (grandes).

Ou seja, você irá implementar seu site ou componente pensando como se estivesse fazendo somente para um celular. Depois você verifica o mesmo em um tablet, e faz as alterações necessarias no breakpoint `md` para o layout ficar de bom. Depois faz o mesmo processo em um desktop pequeno (breakpoint `lg`), e assim por diante até ter feito isso em todos os breakpoints.

Claro, nem sempre você precisará adicionar todos breakpoints pois talvez nem precise. Adicione os breakpoint necessarios para atigir o layout ideal.

### Porque usar mobile first?

Bem, depois de várias experiências que tive adaptando um tela para todos tamanhos de tela, confesso que achei _mobile first_ o melhor até agora. Acho que é muito mais fácil adaptar um layout mobile para desktop do que de adaptar um layout desktop para mobile.

Isso se dá por que ao construir um site voltado para desktop e depois adaptar, você pode acabar tendo que refatorar seu HTML, pois agora você precisa que certo conteúdo vá para baixo, mas como está tudo em uma grande `div`, é preciso quebrar essa mesma em `div`'s menores.

Quando você faz seu layout para mobile, você acaba criando pequeno trechos de HTML que vão montando seu site. E é muito mais fácil reposicionar esses pequenos trechos do que quebrar um HTML grande.

Inclusive, em casos que o layout é feito primerio para desktop, é comum ver if para esconder um layout e mostrar outro, estilo:
```html
<div class="show-only-for-mobile">...</div>

<div class="show-only-for-desktop">...</div>
```

Isso por que as vezes é tão trabalhoso quebrar o layout feito para desktop que os DEVs acabam criando outro layout do zero.

### Flex e grid

Também gostaria de falar sobre [flexbox](https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox) e [grid](https://developer.mozilla.org/pt-BR/docs/Web/CSS/grid), que são maneiras de alinhas e posicionar seus elementos no seu site que podem ajudar a evitar breakpoint ou no mínimo, simplificatos.

Ambos podem ser usados através de:
```css
.my-flex-class {
  display: flex;
}

.my-grid-class {
  display: grid;
}
```

Ambos são ferramentas poderosas que você provavelmente vai usar muito.

Em resumo, flexbox te permite posicionar item lado a lado mais facilmente sem precisa usar o propriedade [`float`](https://developer.mozilla.org/pt-BR/docs/Web/CSS/float) que pode te trazer algumas dores de cabeça. Inclusive, flexbox pode fazer quebras de linhas como: ao exibir uma linha com 4 fotos grandes, se não houver mais espaço na tela, ele joga as imagens que "sairiam da tela" para baixo, sem quebrar seu layout.

Já o display grid, te da mais poderes e permite criar grids (obviamente). Você pode usar tanto para fazer um grid de imagens quando ao alinhar conteúdos mais simples como textos, ou até posicionar seu formulário ou qualquer coisa... enfim, eu diria que sua imaginação é o limite.

Para explicações vou deixar alguns links:

- [Video sobre display flex e grid](https://youtu.be/x-4z_u8LcGc)
- [Guia sobre Flex](https://origamid.com/projetos/flexbox-guia-completo/)
- [Guia sobre Grid](https://www.origamid.com/projetos/css-grid-layout-guia-completo/)

### Páginas não responsivas

Aqui vou deixar algumas página que não são responsivas para ver como seu layout pode quebrar.
Lembre-se de mudar o tamanho de sua tela.

- [Lista de imagens](exemplos/paginas-nao-reponsivas/inline-block/index.html)
- [Card de usuário](exemplos/paginas-nao-reponsivas/card/index.html)
- [My Non-Responsive Web Site](https://dequeuniversity.com/library/responsive/1-non-responsive)

Sobre site mobiles com `.m` na url:
- [Facebook mobile](https://m.facebook.com/)
- [Facebook desktop/default](https://facebook.com/)

### Páginas responsivas

E aqui vou deixar algumas paginas responsivas.

- [Lista de imagens](exemplos/paginas-responsivas/flex-wrap/index.html)
- [Card de usuário](exemplos/paginas-responsivas/card-grid/index.html)
- [Site com colunas](exemplos/paginas-responsivas/cols/index.html)
