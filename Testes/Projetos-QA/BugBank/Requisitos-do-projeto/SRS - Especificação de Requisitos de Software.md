# SRS - Especificação de Requisitos de Software

**Sistema:** BugBank  
**Versão:** 1.0  
**Data:** 03/05/2025  
**Responsável:** Luis Lopes

---

## 1. Visão Geral do Sistema

O BugBank é uma plataforma bancária web que oferece funcionalidades como cadastro de usuários, login, realização de transferências, visualização de extrato, além de funcionalidades futuras como pagamento e saque. Este documento consolida a Especificação de Requisitos de Software (SRS) e o Plano de Testes, promovendo rastreabilidade entre o que deve ser entregue e como será testado.

---

## 2. Módulos Funcionais e Requisitos

### 2.1 Módulo: Login

**Requisitos Funcionais**  
- **RF001:** O sistema deve exigir o preenchimento dos campos **e-mail** e **senha** para tentar login.  
- **RF002:** Se o usuário tentar realizar login sem preencher um ou ambos os campos obrigatórios, o sistema deve exibir a mensagem: "Usuário e senha precisam ser preenchidos".  
- **RF003:** O sistema não deve permitir acesso caso o e-mail e/ou senha informados não correspondam a um usuário previamente cadastrado.  
- **RF004:** Se o usuário informar credenciais válidas, o sistema deve redirecioná-lo para a tela **Home** do sistema.

**Requisitos Não Funcionais**  
- **RNF001:** A autenticação deve ser processada em até **2 segundos**.  
- **RNF002:** As senhas devem ser transmitidas de forma **criptografada**.  
- **RNF003:** A funcionalidade deve ser compatível com **navegadores modernos** (Chrome, Firefox, Edge, Safari).

**Regras de Negócio**  
- A autenticação só será válida se o **par e-mail/senha** corresponder exatamente ao cadastro.  
- O sistema não deve informar qual campo está incorreto.

---

### 2.2 Módulo: Cadastro

**Requisitos Funcionais**  
- Campos **Nome, Email, Senha** e **Confirmação de senha** são obrigatórios.  
- Mensagens exibidas em tentativas de envio sem os respectivos campos:
  - Nome: "Nome não pode ser vazio"
  - Email: "Email não pode ser vazio"
  - Senha: "Senha não pode ser vazio"
  - Confirmação de Senha: "Confirmar senha não pode ser vazio"
- Se a opção "Criar conta com saldo" estiver:
  - Ativada → conta criada com saldo inicial de R$ 1.000,00
  - Inativa → conta criada com saldo de R$ 0,00
- A **senha** e **confirmação de senha** devem ser iguais.
- Cadastro com sucesso deve exibir o **número da conta**.

---

### 2.3 Módulo: Transferência

**Requisitos Funcionais**  
- Transferência apenas para **contas válidas**.  
- **Saldo** deve ser igual ou superior ao valor da transferência.  
- Tentativas com **conta inválida** devem exibir: "Conta inválida ou inexistente".  
- Campos de número e dígito da conta aceitam apenas **números**.  
- **Campo descrição** é obrigatório.  
- **Valor** não pode ser menor ou igual a zero.  
- Ao transferir com sucesso:
  - O valor é **debitado**.
  - Exibe: "Transferência realizada com sucesso".
  - Redireciona para o **extrato**.

---

### 2.4 Módulo: Extrato

- Deve exibir o **saldo disponível**.
- Cada transação exibe:
  - **Data**
