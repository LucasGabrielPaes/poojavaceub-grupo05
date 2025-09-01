'''mermaid

classDiagram
  class Venda {
    -idVenda: int
    -data: Date
    -valorTotal: double
    +calcularTotal() double
    +registrarVenda() void
  }

  Cliente "1" o-- "0..*" Venda:  realiza
  Venda"1" o-- "1" Pedido: gera
  Venda "1" o-- "1..*" Produto: contém
  Funcionario "1" o-- "0..*" Venda: processa
