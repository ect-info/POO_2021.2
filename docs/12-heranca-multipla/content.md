### Programação Orientada a Objetos
#### Herança Múltipla
---

## Objetivo da aula:

- Apresentar o mecanismo de herança múltipla
    - O que é herança múltipla
    - Como utilizá-lo na linguagem Python
---
## Herança:

- Permite que classes derivadas herdem o comportamento
  (atributos e métodos) de uma classe base
- Introduz a relação "é um"
- Código na classe base pode ser __reutilizado__ nas classes derivadas
- Classe derivada pode _reimplementar_ um método com funcionalidades específicas
    - ex.: Tipos de contas bancárias com taxas distintas para realizar o saque

---
## Herança Múltipla
Ocorre quando a classe derivada _possui mais de uma classe base_

Em Python, as classes base são indicadas por uma tupla:

```python
class Subclasse(Superclasse1, Superclasse2):
...
```

- ```Subclasse``` é a classe derivada
- Todos os atributos e métodos de ```Superclasse1```
  e ```Superclasse2``` estão na subclasse

--- 
## Herança Múltipla

Exemplo:

```python
class Superclasse1:
    def metodo_super1(self): ...

class Superclasse2:
    def metodo_super2(self): ...

class Subclasse(Superclasse1, Superclasse2):
    def metodo_sub(self): ...

obj = Subclasse()
obj.metodo_super1()
obj.metodo_super2()
obj.metodo_sub()
```
---
## Herança Múltipla

Os métodos __init__ de cada superclasse precisam ser explicitamente chamados

```python
class Subclasse(Superclasse1, Superclasse2): 
  def __init__(self, valor):
        Superclasse1.__init__(self, 0) # atribui 0 a atrib_super1
        Superclasse2.__init__(self, 1) # atribui 1 a atrib_super2

```

- Também pode ser utilizada apenas uma única chamada com ```super().__init__()```
  (mais sobre isto no Jupyter Notebook)

---
### Herança Múltipla

As superclasses também podem ser classes abstratas

Todos os métodos abstratos de _todas as superclasses_
abstratas têm que ser implementados para que a subclasse
seja __concreta__

 Caso contrário, a subclasse se torna uma classe abstrata

---

Exemplos práticos no [Notebook](12-Heranca-Multipla.ipynb)
---
