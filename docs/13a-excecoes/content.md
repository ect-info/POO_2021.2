### Programação Orientada a Objetos
#### Erros e Exceções
---

### Motivação

Considere os métodos a seguir:

```python
@nome.setter
def nome(self, n):
    '''Set para o nome de uma pessoa'''
    if type(n) == str:
        self._nome = n
    else:
        print('n precisa ser do tipo string')
```

```python
def registraEntrada(self):
    '''Entra um carro'''
    if self.vagas > 0:
        self.vagas -= 1
        print("Um carro entrou.")
    else:
        print("Estacionamento sem vagas")
```
---

### Motivação

- O programa _só imprime_ uma mensagem de erro
- Entretanto, a execução do programa __continua__
- Como fazer para o programa encerrar a sua execução?
- Como __notificar__ de maneira clara que a execução do método não foi bem
  sucedida?
- Como __tratar/detectar__ (por exemplo, no bloco  main) que a execução do método não foi bem sucedida?
---

### Motivação

Estamos interessados em fazer o programa "emitir um erro":

- Emitir erro: notificar **e encerrar o programa**
- O termo técnico para isto em programação é "fazer o programa __levantar uma exceção__"
    - Do inglês "*raise an exception*"
    - Também conhecido em português como "lançar uma exceção" ou "subir uma exceção"
---

### Motivação

Você já deve ter se deparado com alguns erros em Python:

- Índice não valido (fora dos limites): 
>`IndexError: list index out of range`

- Divisão por 0:
> `ZeroDivisionError: division by zero`

- Uma variável inexistente é utilizada:
> `NameError: name x is not defined`

Ou seja, exceções levantadas por programas em Python
---

### Objetivo

Apresentar o mecanismo de tratamento de exceções

- O que é uma exceção
- Como levantar exceções em Python
- Como tratar exceções em Python
- Como implementar classes que representam exceções em Python
---

### Exceções e Tratamento

- Uma _exceção_ é um __erro__ não necessariamente fatal detectável na execução de um programa
    - Diferente de erro de sintaxe
- Para **levantar uma exceção**  utilizamos o comando `raise`
    - `raise Exc`: levanta uma exceção do tipo/classe `Exc`
    - Similar ao comando `throw` de Java e C++
- `Exception` é a _superclasse_ das exceções definidas pelo usuário
- A lista de classes de exceções predefinidas em Python está
  [aqui](https://docs.python.org/3/library/exceptions.html)
---

### Exceções e Tratamento
<img src="python_excecoes.png">

- Imagem de [*Stanford Python Course* (link)](https://drive.google.com/file/d/0B-eHIhYpHrGDWUtObjZ5MDI0dHc/view)
---

### Exemplo

```
class Conta:
    def __init__(self):
        self.__saldo = 0

    def deposito(self, v):
        '''Deposito: v > 0'''
        if v <= 0:
            raise ValueError("Valor de depósito não válido")
        else:
            self.__saldo += v

c = Conta()
c.deposito(3)
c.deposito(5)
c.deposito(0) # ValueError
```
`ValueError`: Tipo de exceção que denota valores de parâmetros não válidos 
--- 

### Tratamento de Exceções

- Após levantada/lançada, uma exceção pode ser **tratada**
- Tratamento de exceções: trecho de código responsável por fazer o programa se
  __recuperar__ da exceção detectada
- De acordo com a _classe/tipo da exceção_, o programa pode tratá-la de forma diferente
- Se a exceção não for tratada, o _tratamento padrão_ é executado:
  imprimir a mensagem de erro na tela e encerrar o programa
---

### Tratamento de Exceções
```[1-4|5-7|9-16|18-27]
class Pessoa:
    def __init__(self, nome=''):
        self._nome = nome

    @property
    def nome(self):
        return self._nome

    @nome.setter
    def nome(self, x):
        '''x deve ser do tipo str'''
        if type(x) == str:
            self._nome = x
        else:
            raise TypeError('Exceção: x precisa ser do tipo str')

if __name__ == '__main__':
    p = Pessoa()
    try:
        n = 3
        p.nome = n # irá levantar erro, já que n não é do tipo str
    except: # cláusula de tratamento de erros:
        print('Ocorreu um erro na leitura dos dados') 
        print('Atribuindo nome em branco') # atribui um nome padrão para pessoa
        p.nome = 'sem nome'
    print(f'Nome: {p.nome}')
```

`TypeError`: Tipo de exceção que denota, dentre outras coisas, um parâmetro com tipo não válido

---
### Try e Except

- A cláusula `try` contém um bloco de código que _pode_ levantar exceções. Ela __tenta__
  executar o bloco de comando nela contido. 
    - Se uma exceção for levantada por uma das linhas dentro do `try`,
      o fluxo do programa é _redirecionado_ para a cláusula `except`
    - As linhas do bloco `try` situadas após a linha de comando que levantou
      a exceção __não são executadas__

```python
try:
    # Tenta executar o bloco
  ...
except: 
    #tratamento
```
---

### Exceções não Tratadas

- Ao levantar uma exceção com ```raise```, a função/método
  não a trata
- Para tratá-la, o código que realiza a chamada à função
  deve fazer isto em um bloco `try`
- Caso nenhuma parte do programa trate uma exceção
  levantada sucessivamente, o Python executa o tratamento padrão
---

### Implementando Classes para Exceções

É possível definir classes para representar exceções personalizadas:

```
class MinhaExcecao(Exception):
    pass
```
---

### Implementando Classes para Exceções

Uma boa prática é:

- Definir uma classe base que herda de ```Exception``` para o seu programa
- Definir erros específicos, que acontecem no domínio do problema em questão, utilizando
  a classe base anterior como o topo da hierarquia (todos os erros herdam dela)
- Desta forma, exceções específicas ao domínio do problema podem ser capturadas
---

### Implementando Classes para Exceções

```
class ErroBasePessoa(Exception):
    pass

class ErroNome(ErroBasePessoa):
    pass

class Pessoa:

 @nome.setter
    def nome(self, x):
        if type(x) == str:
            self._nome = x
        else:
            raise ErroNome('Excecao: x precisa ser do tipo str')
```
---

[Jupyter notebook](./13a-Excecoes.ipynb)
