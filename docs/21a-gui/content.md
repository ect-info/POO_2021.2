### Programação Orientada a Objetos
#### Interfaces Gráficas
---

### Motivação

- A grande maioria dos aplicativos utilizados por nós
  possui uma interface gráfica
    - Janela com vários componentes em que o usuário pode inserir comandos
- Interfaces gráficas melhoram significativamente a usabilidade de um programa
---

### Motivação

- Existem diversas opções de interfaces gráficas em Python:
    - GTK (Gnome Toolkit)
    - QT
    - Wxwidgets
    - etc.
- Na disciplina de POO, iremos trabalhar com a interface gráfica Tk:
    - Tkinter: Tk Interface
    - Interface gráfica desenvolvida para a linguagem de script Tcl
    - Considerada padrão para a linguagem Python
    - Kit de ferramentas com várias opções e de fácil utilização
    - Multiplataforma
---

## Interfaces Gráficas

Programar uma aplicação com interface gráfica requer utilizar
*widgets* (*window gadgets*): componentes de uma interface gráfica

Alguns tipos de widgets:

- *Label* (rótulo)
- Botão
- Campo para entrada de texto
- Barra de menu
- Barra de rolagem
- etc.
---

## Interfaces Gráficas

Desenvolver uma interface gráfica envolve:
- Posicionar e configurar os widgets e suas propriedades (cores, fontes, tamanho, etc.)
- Programar como o sistema deve reagir a eventos ao longo da sua execução:
  - Clique de mouse, movimento de mouse, clique de botão, minimização de janela,
    seleção de texto, seleção de item em uma lista, etc.
---

## Interfaces Gráficas

- Portanto, o desenvolvimento de interfaces gráficas corresponde
  a uma camada a mais no desenvolvimento do programa como um todo
- Em outras palavras: idealmente, o código correspondente à interface gráfica
  deve estar em um módulo separado do código correspondente à lógica do programa
    - Orientação a objetos facilita esta modularização
---

[Jupyter notebook](./14a-GUI.ipynb)
