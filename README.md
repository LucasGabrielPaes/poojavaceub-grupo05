# poojavaceub
#  Loja de Instrumentos Musicais – Modelagem UML

Este projeto é a modelagem de um sistema para uma loja de instrumentos musicais.  
O objetivo é representar as entidades principais, suas relações e comportamentos, utilizando **UML de Classes com Mermaid**.

---

##  Estrutura do Projeto

O sistema foi modelado em arquivos `.md` individuais, cada um representando uma classe obrigatória:

- [Produto.md](./LucasGabriel-Instrumentos.md)  
- [Usuario.md](./Miguel-Usuário.md)  
- [Venda.md](./Duda-Venda.md)  
- [Pedido.md](./Fellipe_pedidos.md)  
- [Fornecedor.md](./Fornecedor.md)  

Cada arquivo contém:
- Descrição da classe  
- Atributos e métodos  
- Papel no sistema  
- Diagrama UML específico da classe (em Mermaid)

---
## Diagrama Geral do Sistema

```mermaid
classDiagram
  %% Usuários
  class Usuario {
    -nome: string
    -cpf: string
    +getDados(): string
    +fazerPedido(): Pedido
  }

  class Cliente {
    -nome: string
    -cpf: string
    +getDados(): string
    +fazerPedido(): Pedido
  }

  class Funcionario {
    -nome: string
    -matricula: string
    +registrarPedido(p: Pedido): void
    +emitirNota(): string
  }

  %% Produtos
  class Produto {
    -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
  }

  class Instrumento {
    +tipo: string
    +tocar(): void
    +getCategoria(): string
  }

  class Cordas {
    +afinar(): void
    +tocarAcorde(): void
  }

  class Metais {
    +limpar(): void
    +soprar(): void
  }

  class Percussao {
    +bater(): void
    +ritmar(): void
  }

  class Acessorio {
    +tipo: string
    +usar(): void
    +getInfo(): string
  }

  %% Operações
  class Pedido {
    -numero: int
    -data: date
    -status: string
    +getTotal(): float
    +adicionarProduto(p: Produto): void
  }

  class Venda {
    -idVenda: int
    -data: date
    -valorTotal: double
    +calcularTotal(): double
    +registrarVenda(): void
  }

  class Fornecedor {
    -nome: string
    -cnpj: string
    +fornecerProduto(): Produto
    +getInfo(): string
  }

  %% Relações
  Usuario <|-- Cliente
  Usuario <|-- Funcionario

  Produto <|-- Instrumento
  Produto <|-- Acessorio

  Instrumento <|-- Cordas
  Instrumento <|-- Metais
  Instrumento <|-- Percussao

  Pedido "1" --> "*" Produto
  Pedido "*" --> "1" Cliente

  Venda "1" --> "1" Pedido
  Venda "1" --> "1" Cliente
  Venda "1" --> "1" Funcionario

  Fornecedor "1" --> "*" Produto
```
