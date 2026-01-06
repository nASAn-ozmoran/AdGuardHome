# Primeiro app de teste, passo a passo

Rode:

```
npx create-expo-app lanterna-verde -t
```

Na sequência, escolha o modelo em branco com TypeScript.

A pasta com o nome informado no comando é criada; entre nela:

```
cd lanterna-verde
```

Depois suba o servidor de desenvolvimento:

```
npm run start
```

O terminal mostra um código de barras quadrado, que foi lido pelo aplicativo no celular.

Sobre as etiquetas do tipo campo de texto, a orientação em aula é que tudo precisa ser importado — a primeira linha da imagem mostra isso.

![needs-import](images/imports-necessarios.png)

A imagem também mostrou como definir estilo embutido no próprio elemento.

Os componentes foram comparados a peças de montar: a documentação serve tanto para consultar detalhes de um componente quanto para procurar algo que sirva à ideia que você tem.

![documentation](images/documentacao.png)

O código final do primeiro app ficou assim:

![first-app-txt](images/primeiro-app.png)

O resultado era exibido no espelhamento do celular na tela do computador.

Também foi mostrado que texto solto, fora de um componente de texto, gera erro na aplicação.

![text outside a component](images/texto-fora-de-componente.png)

Comentário da aula: todo componente começa com letra maiúscula.

A documentação mostra as duas formas de declarar: por classe ou por função.

![component based on a class or on a function](images/componente-classe-ou-funcao.png)

Componentes de classe eram o padrão no passado; hoje é mais comum declarar por função.

Como aparece numa das imagens, a linha de exportação padrão declara uma função que devolve **um único** componente. Devolver mais de um componente externo quebra a aplicação. Exemplo (**errado**):

![more than 1 external components](images/dois-componentes-externos.png)


# Estilos

Os estilos podem ser embutidos ou vir de um objeto separado. O embutido usa chaves duplas e o outro usa chave simples. Veja:

![inline or not styles](images/estilos.png)

A forma de declarar propriedades lembra CSS.

Dá para acumular várias declarações, separando cada uma por vírgula. Veja a imagem:

![several styles using quotes](images/varias-configuracoes.png)

Para reunir várias configurações num objeto nomeado, use o criador de folha de estilos. Veja:

![Stylesheet.create](images/folha-de-estilos.png)

Algumas diferenças em relação a CSS:

- As declarações são separadas por vírgula, não por ponto e vírgula;
- As propriedades ficam em formato camelo, sem hífen.

Não esqueça de importar o criador de folha de estilos:

![importing Stylesheet](images/importando-folha.png)


# Comentários

Comentários entram entre chaves com a marcação de bloco. A justificativa da aula é que **no mundo do React Native tudo é objeto**.

![comment example](images/exemplo-de-comentario.png)


# Imagens

A documentação do componente de imagem foi apresentada:

![Image component in documentation](images/componente-imagem.png)

E um exemplo de aplicação carregando uma imagem:

![example - loading an image](images/exemplo-carregando-imagem.png)

Foram necessários três passos:

- **1:** importar o componente de imagem (topo do exemplo acima);
- **2:** importar o arquivo da imagem informando o caminho;
- **3:** usar o componente com a propriedade de origem apontando para o valor importado no passo 2.

Alternativamente, dá para informar o caminho direto no atributo:

![specifying image path directly](images/caminho-direto.png)

Repare que nesse caso a propriedade recebe chaves duplas.


# Evitando um aviso no editor

O aviso vem do sistema de tipos da linguagem, que não reconhece a extensão da imagem como um tipo conhecido.

![warning no png type](images/aviso-de-tipo.png)

Basta criar um arquivo de declaração de tipos com uma linha declarando o módulo da extensão:

![index.d.ts](images/declaracao-de-tipos.png)


# Recarregando quando a imagem não aparece

Se a imagem não carregar, pare o servidor, suba de novo com o mesmo comando e, no terminal, use a opção de recarregar.

![reloading app](images/recarregando.png)


# Informações soltas

## Preencher a área

Use a propriedade de flexão com valor 1 para a imagem ocupar tudo. Sem ela, quando estilizando:

![without flex: 1](images/sem-flexao.png)

Com ela:

![without flex: 1](images/com-flexao.png)


## Alinhamento vertical

Use o alinhamento de conteúdo no centro. Sem essa propriedade:

![without justifyContent: 'center'](images/sem-centralizacao.png)

Com ela:

![with justifyContent: 'center'](images/com-centralizacao.png)


## Alinhamento horizontal

Use o alinhamento de itens no centro. Sem essa propriedade:

![without alignItems:center](images/sem-alinhamento-itens.png)

Com ela:

![with alignItems: 'center'](images/com-alinhamento-itens.png)


# Trocar imagem conforme uma variável

Veja a imagem:

![changing image source depending on a variable](images/origem-dinamica.png)


# Estilos condicionais

Declarando:

![configuring a conditional style](images/declarando-estilo-condicional.png)

Usando:

![using a conditional style](images/usando-estilo-condicional.png)


# Área tocável

A imagem que precisa responder ao toque deve ficar dentro do contêiner de toque. Não esqueça de importá-lo. Veja:

![Touchable opacity](images/area-tocavel.png)


## Ação de clique na área tocável

Para exibir mensagem no terminal:

![using onclick on Touchable Opacity to show a message in terminal](images/clique-exibindo-mensagem.png)

Evidentemente, no lugar da função anônima você pode passar uma função já declarada:

![using onclick on Touchable Opacity with a handler function](images/clique-com-funcao-de-tratamento.png)


# Hooks e estado

Se um tratador de clique muda um valor ligado a uma variável e esse valor define o estilo de um elemento, a mudança não aparece: é preciso usar estado.

A importação fica assim:

```
import React, {useState} from 'react';
```

E o uso:

![useState](images/estado.png)

Notas:
- Curioso, o valor alterado é de uma **constante**;
- A ordem dos nomes é: variável de estado, função que altera, e o valor inicial entre parênteses.

Mas onde entra o toque? No tratador de clique da área tocável.

![click handler - TouchableOpacity](images/tratador-de-clique.png)


# Repositório do capítulo

O código usado neste capítulo está num repositório público da trilha.


# Link externo indicado em aula

A documentação do componente de botão da biblioteca padrão.