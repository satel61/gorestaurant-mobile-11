# Desafio 11: GoRestaurant Mobile


![GO RESTAURANT MOBILE](https://github.com/satel61/gorestaurant-mobile-11/blob/master/gorestaurant-mobile.gif)

## Sobre o desafio

Nesse desafio, você irá desenvolver mais uma aplicação, a GoRestaurant, só que dessa vez a versão mobile para o cliente. Agora você irá praticar o que você aprendeu até agora no React Native junto com TypeScript, para criar um pequeno app para pedidos de comida.

Essa será uma aplicação que irá se conectar a uma Fake API, e exibir e filtrar os pratos de comida da API e permitir a criação de novos pedidos.

## Layout da aplicação

https://www.figma.com/file/cHzfYrUBgdzp1XrRuUpggk/GoRestaurant-Mobile?node-id=1603%3A448

## Utilizando uma fake API

Antes de tudo, para que você tenha os dados para exibir em tela, criamos um arquivo que você poderá utilizar como fake API para te prover esses dados.

Para isso, deixamos instalado no seu package.json uma dependência chamada json-server, e um arquivo chamado server.json que contém os dados para as seguintes rotas:

__Rota /foods:__ Retorna todas as comidas cadastradas na API

__Rota /foods/:id:__ Retorna um prato de comida cadastradas na API baseado no id

__Rota /categories:__ Retorna todas as categorias cadastradas na API

__Rota /orders:__ Retorna todas os pedidos que foram cadastrados na API

__Rota /favorites:__ Retorna todas as comidas favoritas que foram cadastrados na API

```
  yarn json-server server.json -p 3333
```

## Funcionalidades da aplicação


__Listar os pratos de comida da sua API:__ Sua página Dashboard deve ser capaz de exibir uma listagem, com o campo name, value e description de todos os pratos de comida que estão cadastrados na sua API.

__Listar as categorias da sua API:__ Sua página Dashboard deve ser capaz de exibir uma listagem, com o campo title e image_url de todas as categorias que estão cadastrados na sua API.

__Dica:__ O campo thumbnail_url será utilizada como imagem da categoria, deixamos três categorias como exemplo no arquivo server.json.

__Filtrar pratos de comida por busca ou por categorias:__ Em sua página Dashboard permitir que o input de pesquisa e os botões de categoria façam uma busca na API de acordo com o que estiver selecionado ou escrito no input.

__Listar os pedidos da sua API:__ Sua página Orders deve ser capaz de exibir uma listagem, com o campo as informações do produto pedido, com name e description de todos os pedidos que estão cadastrados na sua API.

__Dica:__ Por se tratar de uma Fake API e de não possuir usuários, não será necessário cadastrar o campo user_id, considere que deve ser listados todos os pedidos da API como se fossem os seus pedidos.

__Listar os pratos favoritos da sua API:__ Sua página Favorites deve ser capaz de exibir uma listagem, com o campo as informações do produto favorito, com name e description de todos os pedidos que estão cadastrados na sua API.
__Dica:__ Por se tratar de uma Fake API e de não possuir usuários, não será necessário cadastrar o campo user_id, considere que deve ser listados todos os favoritos da API como se fossem os seus favoritos.

__Realizar um pedido:__ Na sua página Dashboard, ao clicar em um item, você deve redirecionar o usuário para a página FoodDetails, onde será possível realizar um novo pedido, podendo controlar a quantidade desse item pedido, ou adicionar ingredientes extras. Todo o valor deve ser calculado de acordo com a quantidade pedida.
__Dica:__ Você pode usar o método reduce para somar o valor de todos os extras pedidos e somá-lo com o valor do prato de comida. Depois disso lembre-se de multiplicar tudo pela quantidade pedida do produto.

## Específicação dos testes

Para esse desafio, temos os seguintes testes:

__should be able to list the food plates:__ Para que esse teste passe, sua aplicação deve permitir que sejam listados na sua Dashboard, todos os pratos de comidas que são retornados da sua fake API.

__hould be able to list the food plates filtered by category:__ Para que esse teste passe, sua aplicação deve permitir que sejam listados na sua Dashboard, os pratos de comidas filtrados por categoria da sua fake API.

__Dica:__ No json-server você pode usar os query params normalmente para buscar/filtrar de acordo com o valor de um campo do item no arquivo server.json. Por exemplo, para filtrar todos os pratos com a categoria 1, a sua url ficaria como http://localhost:3000/foods?category_like=1.

__should be able to list the food plates filtered by name search:__ Para que esse teste passe, sua aplicação deve permitir que sejam listados na sua Dashboard, os pratos de comidas filtrados por nome da sua fake API.
__Dica:__ No json-server você pode usar os query params normalmente para buscar/filtrar de acordo com o valor de um campo do item no arquivo server.json. Por exemplo, para filtrar todos os pratos com o nome Veggie, a sua url ficaria como http://localhost:3000/foods?name_like=Veggie.

__should be able to navigate to the food details page:__ Para que esse teste passe, em sua Dashboard, você deve permitir que ao clicar em um item, seja navegado para a página FoodDetails passando por parâmetro da navegação o id do item clicado.

__should be able to list the favorite food plates:__ Para que esse teste passe, sua aplicação deve permitir que sejam listados na sua página Favorites, todos os pratos de comidas que estão salvos na rota favorites.

__should be able to list the orders:__ Para que esse teste passe, sua aplicação deve permitir que sejam listados na sua página Orders, todos os pratos de comidas que estão salvos na rota orders.

__should be able to list the food:__ Para que esse teste passe, sua aplicação deve permitir que seja listado todos os dados de uma comída específica na página FoodDetails, baseado no id recuperado pelos parametros da rota.

__Dica 1:__ Use o hook useRoute para pegar o atributo params que conterá o id enviado por parametro.

__Dica 2:__ Com o id recuperado por parametro da navegação, faça uma busca na sua API com os dados atualizados da food na roda /foods/:id.

__should be able to increment food quantity:__ Para que esse teste passe, você deve permitir que seja incrementada em 1 a quantidade do item na página FoodDetails.

__should be able to decrement food quantity:__ Para que esse teste passe, você deve permitir que seja decrementada em 1 a quantidade do item na página FoodDetails.

__Dica:__ Não permita que o valor do input seja alterado para menor que 1, para que assim o pedido sempre tenha no mínimo um item.

__should not be able to decrement food quantity below than 1:__ Para que esse teste passe, você deve impedir que seja decrementado a quantidade de itens até um número menor que 1, assim o número mínimo de itens no pedido é 1.

__should be able to increment an extra item quantity:__ Para que esse teste passe, você deve permitir que seja incrementada em 1 a quantidade de um ingrediente extra na página FoodDetails baseado no seu id.

__should be able to decrement an extra item quantity:__ Para que esse teste passe, você deve permitir que seja decrementado em 1 a quantidade de um ingrediente extra na página FoodDetails baseado no seu id.
