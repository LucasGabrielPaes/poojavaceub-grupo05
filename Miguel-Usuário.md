# Classe Usuário

No sistema da loja de instrumentos musicais, a classe **Usuário** representa qualquer pessoa que acessa o sistema.  
Ela é **abstrata** e se especializa em dois tipos principais: **Cliente** (quem compra) e **Funcionário** (quem processa vendas).

---

## Atributos
### Usuário
- `id : int` → Identificador único.  
- `nome : String` → Nome completo.  
- `email : String` → E-mail de acesso.  
- `senha : String` → Senha de autenticação.  

### Cliente (herda de Usuário)
- `cpf : String` → Cpf do cliente.  
- `telefone : String` → Contato do cliente.  

### Funcionário (herda de Usuário)
- `matricula : String` → Código de identificação do funcionário.  
- `cargo : String` → Função (ex: vendedor, gerente).  

---

## Métodos
### Usuário
- `autenticar( senha: String) : boolean` → Retorna se o login foi válido.  
- `visualizarPerfil() : String` → Retorna dados básicos do usuário.  

### Cliente
- `realizarPedido(produto: Produto, quantidade: int) : Pedido` → Cria um pedido.  
- `consultarHistorico() : List<Pedido>` → Retorna os pedidos já feitos.  

### Funcionário
- `registrarVenda(venda: Venda) : boolean` → Registra uma venda no sistema.  
- `atenderCliente(cliente: Cliente) : void` → Atende o cliente e processa seu pedido no sistema.  

---

## Diagrama UML - USUÁRIO

```mermaid
classDiagram
  class Usuario {
    -id: int
    -nome: String
    -email: String
   
    +autenticar(senha: String) boolean
    +visualizarPerfil() String
  }

  class Cliente {
    -cpf: String
    -telefone: String
    
    +realizarPedido(produto: Produto, quantidade: int) Pedido
    +consultarHistorico() List<Pedido>
  }

  class Funcionario {
    -matricula: String
    -cargo: String
    +registrarVenda(venda: Venda) boolean
    +atenderCliente(cliente: Cliente) void
  }

  Usuario <|-- Cliente
  Usuario <|-- Funcionario

  Cliente "1" --> "0..*" Pedido : realiza
  Funcionario "1" --> "0..*" Venda : registra


