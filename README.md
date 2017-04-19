# Curso Refatoração para JS(Jean Suissa) Funcional

Esse curso também servirá como manual de regras para os meus alunos, todo código que eu ver e não seguir essas definições eu pedirei educadamente para refatorar baseando-se nesse manual de boas praticas do JS Funcional.

## O Curso

Esse curso iria sair gratuitamente, porém por acasos da vida estou necessitado de certa quantia monetaria para quitar umas dívidas, então um aluno me sugeriu pedir como doação mas logo me veio a mente que poderia, mesmo nao querendo, cobrar pelo próximo conteúdo que estava criando. 

Como a maioria que me conhece, sabe que todos meus conteúdos sao gratuitos. Logo quando a meta for alcançada irei liberar 
para todos o curso que contara' com um certificado emitido pela Webschool.

- custo: R$35
- meta: 100 alunos
- data: quando alcançar a meta


### Ementa

- (Por que|Quando|Onde) usar Programaçao Funcional?
- Como eliminar efeitos colaterais
- Como iterar em *arrays* da forma correta
- Como e por que utilizar dados imutaveis
- Refatorando nossos códigos antigos para JS Funcional

ps: Óbviamente veremos **muitooooo** `map`, `filter` e `reduce`, fora outras funções nao muito conhecidas!

### Tempo

O curso será gravado entre 4 a 6 hora e será disponibilizado **apenas** após termos 100 alunos. Logo esse curso nao terá uma data de lançamento definida, o lançamento ocorrerá quando atingirmos a meta de alunos.

### Inscriçao

Para se inscrever basta abrir uma *issue* nesse repositório com seus seguintes dados:

- Email
- Facebook/Twitter
- Telegram

Que entrarei em contato para passar a forma de pagamento.


### Forma de pagamento

Será feito via depósito diretamente na minha conta, ou se quiser via Paypal custara' R$40. 

> **Nada daquele lixo do Pagseguro!**


## Regras para um código mas funcional

Escreverei mais regrinhas no decorrer da gravação das aulas.


### push

> Sabe onde é o único lugar que vc **DEVE** usar o no `reduce` para *array*.

```js

const toListOfObjects = ( acc, cur ) => {
  acc.push({ index: cur})
  return acc
}
[1, 2, 3, 4].reduce( toListOfObjects, [] )
//[ { index: 1 }, { index: 2 }, { index: 3 }, { index: 4 } ]

```

> **Sabe o porquê não posso retornar o `push`?**

```js

> [].push(1)
1

```

> Não preciso explicar neh?

Vamos ao que interessa, esse código abaixo eu vejo direto, portanto agora só mandarei esse texto 
para o *dev* corrigir seu código.

```js

var profiles = getProfiles() // vem um array cabuloso

var arr = []

for (let i = 0; profiles.length > i; i++) {
  arr.push(profiles[i].name)
}

```

> Var!!?? Eh sério mesmo que ainda é usado??!!

**SEMPRE** que você tiver um *array* e precisar iterar nele para pegar ou modificar valores, 

**PELO AMOR DE ODIN USE MAP!!!!**

Já escrevi alguns conteudos sobre o dito cujo, depois link aqui.

**Refatorando para o jeito certo:**

```js

const profiles = getProfiles() // vem um array cabuloso

const profilesNames = profiles.map( ( profile ) => profile.name )

```

Semantificando o code:


```js

const toNames = ( profile ) => profile.name 
const profilesNames = getProfilesAnd().map( toNames )

```

### forEach



### Como sei o que usar?

Percebo que a maior dificuldade dos meus alunos é nao saber qual a funçao correta aplicar, portanto irei explicar
da forma mais suave na nave possível.


#### Map

Quando vc precisar modificar valores ou selecionar apenas alguns, porém o **resultado sempre ter´a o mesmo tamanho
do *array* inicial**, lembre bem disso que ir´a lhe poupar muito tempo!

#### Filter

Quando vc quer selecionar apenas determinados elementos baseados em um teste lógico, ou seja, se a funçao do `filter`
retornar `true` esse elemento sera adicionado no *array* resultante. Portanto **o *array* final provavelmente sera menor que o inicial**. 

> Oia aí!


#### Reduce

> Serve p/ qquer coisa. LOL

![](http://www.jewellex.co.za/userfiles/Brinks%20Logo(1).jpg)
