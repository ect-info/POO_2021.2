### Programação Orientada a Objetos
#### Encapsulamento
---

### Revisão 

#### Classe
Abstração para agrupar objetos comuns

Descreve de maneira _abstrata_ o comportamento dos

#### Objetos 
*Instâncias* de uma classe

Encapsulam um _estado_
---

### Revisão 

- _Atributos_: características da entidade sendo modelada
- _Métodos_: definem o *comportamento*
- _Inicializaodor_: inicializa os atributos (construtor em outras linguagens)
- `self`: referência que um objeto tem dele mesmo
---

### Objetivos

Nesta aula aprenderemos:
  - _Encapsulamento_: __segundo pilar__ de POO
  - Setters/getters e `@property`: primeiro decorador em Python
---

### Encapsulamento

> Capacidade de esconder informações (dados) nos objetos

- __Proteger__ o acesso (externo à classe) a alguns atributos de um objeto
    - Membros que não devem ser usados fora da classe devem estar *escondidos*
      de quem irá utilizar a classe
- As classes devem __expôr o mínimo necessário__ para serem utilizadas
    -  Similar a funções: os dados mínimos que elas precisam são os parâmetros
---

### Encapsulamento

- POO é comumente utilizada no desenvolvimento de bibliotecas
- Os usuários da classe só podem acessar os membros e métodos  *públicos* da classe.
    - **Importante**: usuário do sistema não é o usuário da classe
    - O usuário da classe é quem utiliza o código POO em seu código
- Ao chamar um método, podemos ignorar como ele foi implementado
- Facilita a manutenção e reaproveitamento do código
---

### Modificadores de Acesso

Os __modificadores de acesso__ valem para atributos e métodos:

- __Público__:  o atributo/método pode ser acessado/chamado de dentro ou
  fora da classe
- __Privado__: o atributo/método só pode ser acessado/chamado de dentro da
  classe; ele não é herdado pelas subclasses
- __Protegido__: o atributo/método só pode ser acessado/chamado de dentro da
  classe; ele é herdado pelas subclasses

> A implementação dos modificadores é um mecanismo dependente da linguagem. Em C++ e
Java, por exemplo, as palavras chaves `public` e `private` devem ser usadas
para esta função

---

### Modificadores de Acesso
#### Exemplo em Java

```java
public class Pessoa{
    // Atributos
    private String nome;
    private int idade;
    // Método público
    public String cumprimentar(Pessoa outro)
    {...
    }
}
```

Em Python, não é assim que funciona. Mais sobre isto no
notebook da aula. 
---

### Exemplo: Estacionamento
- Um estacionamento tem capacidade para um número n > 0 de vagas. 
- Devemos controlar quantos carros estão dentro do estacionamento. 
- Os carros podem entrar só se há vagas disponíveis.

Nesse sistema podemos identificar:
- _Classes_: Carros e o Estacionamento (por enquanto, vamos ignorar os carros)
- _Atributos_: número de vagas, capacidade máxima
- _Métodos_: Os carros podem _entrar_ e _sair_. Além disso, podemos consultar o número de vagas disponíveis.
--- 

### Exemplo: Estacionamento
Os usuários da classe `Estacionamento` deveriam __modificar diretamente__  o atributo `vagas`? 

*Não!*   O valor do atributo _vagas_ não deve ser modificado diretamente (isto
deve ser feito utilizando os método `entrar`/`sair`).
---

### Encapsulamento
Utilizado para:
- *Esconder* os membros de uma classe
- *Esconder* como funcionam as rotinas (métodos) da classe
- *Facilitar o reaproveitamento* de código
- *Garantir a consistência* (do estado) dos objetos

> As classes devem expor o mínimo necessário para serem utilizadas
---

### Encapsulamento em Python
[04-Encapsulamento](04-Encapsulamento.ipynb)
