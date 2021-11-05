### Programação Orientada a Objetos
#### Relações entre Classes
---

### Revisão 

#### Classe
> - Abstração para agrupar objetos comuns
> - Descreve de maneira _abstrata_ o comportamento dos objetos 

#### Objetos 
> - *Instâncias* de uma classe
> - Encapsulam um _estado_
---

### Revisão
- _Construtor_: inicializa o objeto com valores iniciais para os atributos
- _Atributos_: características da entidade sendo modelada
- _Métodos_: definem o __comportamento__ através de funções que objetos
da classe executam
- `self`: referência ao próprio objeto
---

### Interfaces e Encapsulamento
#### Membros privados

> - Métodos e atributos que _não devem ser visíveis_ para os usuários da classe
> - Utilizados apenas internamente (no corpo da classe)

#### Membros Públicos

> - Métodos que podem ser chamados _externamente_
> - Especificam um _contrato_: operações que o objeto pode e deve realizar
---

### Interfaces e Encapsulamento

> - Alterações no estado de um objeto acontecem através da _chamada de seus métodos_
> - As mudanças na implementação não devem afetar os usuários da classe
---

### Aula de Hoje

> As classes _não existem sozinhas_: elas têm _relacionamentos
> entre si_ que descrevem como os objetos __interagem uns com os outros__

Objetivos desta aula:

- Introduzir o conceito de diagrama de classes
- Explicar como os objetos _se relacionam_ em um sistema orientado a objetos
- Identificar os diferentes _tipos de relacionamento_ entre classes
- Implementar relações entre classes em Python
---

### Implementação de Classes

- Até então, vocês implementaram uma (ou no máximo duas) classes
  para os programas implementados
- A partir desta aula, deverá ficar claro quando mais de uma classe
  se torna necessário e qual o papel de cada uma delas
    - Como elas se relacionam entre si 
- Antes disto, para facilitar:
    - Como mostrar/visualizar rapidamente o que possui uma classe?
---

### Diagrama de Classe UML

<img src="./img/classe_pessoa1.png" width=250 />

Blocos representam classes:
- Parte superior: atributos
- Parte inferior: métodos, com tipo de parâmetros e tipo de retorno
- `-` denota um membro de classe _privado_
- `+` denota um membro _público_
---

### Diagrama de Classe UML

Diagrama de classe da linguagem unificada de modelagem (UML)
- Facilita a visão geral de sistemas maiores
- Ferramenta: [Draw IO](https://www.draw.io/)
---

### Relacionamentos de Associação 
- Indicam algum _relacionamento_ significativo e de interesse entre objetos
- Especificam que objetos de uma classe estão de alguma forma associados a objetos de outras classes 

Exemplos:
- Em um `Estacionamento` estão _estacionados_ os `Carros`
- Um `Professor` _ministra_ várias `Disciplinas`
- Uma `Mensagem` _possui_ um `Remetente` e um `Destinatário`
---

### Relacionamentos de Associação 
<img src="./img/multiplicidade.png" width="450"/>

Notação de _associação_ em diagrama de classes: **linha** conectando as classes que estão associadas
- Um objeto tipo A está associado com zero ou vários objetos tipo B
- Um objeto tipo B está associado com um objeto tipo A
---

### Multiplicidade:
Nas extremidades da linha denotando a associação, está a _multiplicidade_:
 - `0` : zero
 - `0..1`: zero ou um
 - `1` : um
 -  `1..*`: um ou mais
 - `0..*` ou `*`: zero ou mais
---

### Relacionamentos de Associação
#### Exemplo

Um banco, no qual cada conta bancaria está relacionada com uma pessoa (o
titular da conta):

<img src="./img/pessoa_X_conta.png" width=400/>

Observe que este diagrama representa uma lógica de negócio específica:
- Uma pessoa pode ter mais de uma conta?
- É possível existirem contas conjuntas?
---

### Relacionamentos de Agregação

- Representa uma relação _todo-parte_ **fraca**
- __As partes podem existir sem o todo__

Exemplos:
 - Considere a relação entre o `Carro`, as `Rodas` e o `Motor`
 - Considere a relação entre um `Computador`,  o `Teclado`, a `Tela`
---

### Relacionamentos de Agregação

<img src="./img/agregacao.png" />

Notação da _agregação_ em diagrama de classes: diamante vazado na classe que representa o todo juntamente com linha conectando as classes
- A é o __todo__
- B são as __partes__
---

### Relacionamentos de Agregação
#### Exemplo

Um carro que possui 1 motor e 4 rodas

<img src="./img/carro_X_rodas_X_motor.png" width=500 />
---

### Relacionamentos de Agregação

Com agregação:
- Objetos do tipo `Motor` e `Roda` são instanciados
- Estas instâncias são associadas a um objeto do tipo `Carro` quando
um `Carro` é inicializado
- Ou seja, `Motor`, `Roda` e `Carro` podem ser 
__instanciados independentemente__
- Quando a instância de `Carro` é removida da memória, as instâncias de `Motor` e `Roda` associadas ao objeto removido continuam a existir
---

### Relacionamentos de Composição

- Representa  uma relação _todo-parte_ **forte**
- Se o objeto _todo_ deixar de existir, os seus objetos _parte_ também devem deixar de existir

Exemplos:
- Um `Estacionamento` e seus `Andares`
- Um `Prédio` e suas `Salas`
---

### Relacionamentos de Composição

<img src="./img/composicao.png" width=400/>

Notação da _composição_ em diagrama de classes:
diamante preenchido na classe que representa o todo
juntamente com linha conectando as classes
- A é o __todo__
- B são as __partes__
- Quando o todo é instanciado, as partes também são
---

### Relacionamentos de Composição
#### Exemplo

Prédio com várias salas

<img src="./img/predio_X_sala.png" width=500 />
---

### Relacionamentos de Composição

Com composição:
- Objetos do tipo `Predio` são instanciados e,
  dentro do seu inicializador, instanciam objetos
  da classe `Sala`
- Ou seja, `Predio` instancia `Sala` automaticamente
  - Não é possível criar um `Predio` sem que suas `Salas`
    sejam criadas
  - Quando a instância de `Predio` é removida da memória, as instâncias de
    `Sala` também são removidas
---

### Resumindo
#### Associação
- Modela uma relação genérica entre duas classes
- Nenhum objeto é considerado dono/proprietário do outro objeto

#### Agregação
- Modela uma relação do tipo *tem um* fraca: um objeto da classe A *tem um* (ou mais) objeto da classe B
- Objetos da classe A podem existir sem que objetos da classe B existam
    - Observe que neste caso, o objeto da classe A pode não estar pronto para uso (estado inconsistente)
---

### Resumindo
#### Composição
- Modela uma relação do tipo *tem um* forte: um objeto da classe A *tem um* (ou mais) objeto da classe B
- Objetos da classe A quando instanciados instanciam também objetos da classe B
- Objetos da classe B deixam de existir quando objetos da classe proprietária A
deixam de existir
---

### Relações entre Objetos e Abstração
- A escolha de uma forma de relação específica
  está atrelada à abstração empregada no domínio
  do problema
- As classes ```Motor```, ```Roda``` e ```Carro```,
  por exemplo:
    - Podem ser implementadas como agregação em um sistema:
      é interessante que ```Motor``` e ```Roda``` sejam instanciados
      sem depender de um ```Carro```
    - Podem ser implementadas como composição em um outro sistema:
      ```Motor``` e ```Roda``` só podem ser instanciados
      quando um ```Carro``` é instanciado
---

### Relações entre Classes
[06-relacoes](06-Relacoes.ipynb)
