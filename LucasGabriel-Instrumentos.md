```mermaid
classDiagram
  class Produtos {
     -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
  }

class instrumentos {
   -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
}


  class instrumentos De Cordas {
   -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
}

 class instrumentos De Sopros {
   -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
}

 class instrumentos De Percussoes {
   -nome: string
    -preco: float
    +getPreco(): float
    +getDescricao(): string
}
Produtos --|> instrumentos
instrumentos "1" --> "*" instrumentos De Cordas : tem
instrumentos "1" --> "*" instrumentos De Sopros : tem
instrumentos "1" --> "*" instrumentos De Percussoes : tem
```
