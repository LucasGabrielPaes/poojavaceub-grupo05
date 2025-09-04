# Classe Usuário

No sistema da loja de instrumentos musicais, a classe **Usuário** representa qualquer pessoa que acessa o sistema.  
Ela é **abstrata** e se especializa em dois tipos principais: **Cliente** (quem compra) e **Funcionário** (quem processa vendas).

---

## Atributos
### Usuário
- `id : int` → Identificador único.  
- `nome : String` → Nome completo.  
- `email : String` → E-mail de acesso.  
+ `login() boolean : String` → Login de autenticação.
+ `logout() void : String ` → Logout do usuario

### Cliente (herda de Usuário)
- `endereco : String` → Endereço de entrega.  
- `telefone : String` → Contato do cliente.  

### Funcionário (herda de Usuário)
- `matricula : String` → Código de identificação do funcionário.  
- `cargo : String` → Função (ex: vendedor, gerente).  

---

## Métodos
### Usuário
- `autenticar(email: String, senha: String) : boolean` → Retorna se o login foi válido.  
- `visualizarPerfil() : String` → Retorna dados básicos do usuário.  

### Cliente
- `realizarPedido(produto: Produto, quantidade: int) : Pedido` → Cria um pedido.  
- `consultarHistorico() : List<Pedido>` → Retorna os pedidos já feitos.  

### Funcionário
- `registrarVenda(venda: Venda) : boolean` → Registra uma venda no sistema.  
- `emitirRelatorio() : String` → Gera um resumo das vendas realizadas.  

---

## Diagrama UML - USUÁRIO

```mermaid
classDiagram
  class Usuario {
    -id: int
    -nome: String
    -email: String
    -senha: String
    +autenticar(email: String, senha: String) boolean
    +visualizarPerfil() String
  }

  class Cliente {
    -endereco: String
    -telefone: String
    +realizarPedido(produto: Produto, quantidade: int) Pedido
    +consultarHistorico() List<Pedido>
  }

  class Funcionario {
    -matricula: String
    -cargo: String
    +registrarVenda(venda: Venda) boolean
    +emitirRelatorio() String
  }

  Usuario <|-- Cliente
  Usuario <|-- Funcionario

  Cliente "1" --> "0..*" Pedido : realiza
  Funcionario "1" --> "0..*" Venda : registra

