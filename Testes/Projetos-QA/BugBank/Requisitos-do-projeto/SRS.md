# SRS - Especificação de Requisitos de Software  
## Módulo: Login  
### Sistema: BugBank  
**Versão:** 1.0  
**Data:** 03/05/2025  
**Responsável:** [Seu nome aqui]

---

## 1. Visão Geral
A funcionalidade de login tem como objetivo permitir que usuários previamente cadastrados acessem o sistema BugBank, mediante autenticação via email e senha. O sistema deve validar as credenciais e direcionar o usuário autenticado à tela principal (home).

---

## 2. Requisitos Funcionais

### RF001 - Campos obrigatórios
- O sistema deve exigir o preenchimento dos campos **Email** e **Senha** para tentar login.

### RF002 - Validação de campos vazios
- Se o usuário tentar realizar login sem preencher um ou ambos os campos obrigatórios, o sistema deve exibir a mensagem:  
  **"Usuário e senha precisam ser preenchidos"**.

### RF003 - Validação de credenciais
- O sistema **não deve permitir** acesso caso o email e/ou senha informados **não correspondam a um usuário previamente cadastrado**.

### RF004 - Redirecionamento após login bem-sucedido
- Se o usuário informar credenciais válidas, o sistema deve redirecioná-lo para a tela **Home** do sistema.

---

## 3. Requisitos Não Funcionais

### RNF001 - Tempo de resposta
- A autenticação deve ser processada em até **2 segundos** após o envio das credenciais.

### RNF002 - Segurança
- As senhas devem ser transmitidas de forma **criptografada** (HTTPS obrigatório).

### RNF003 - Compatibilidade
- A funcionalidade deve estar disponível em **navegadores modernos** (Chrome, Firefox, Edge, Safari).

---

## 4. Regras de Negócio

- A autenticação só será considerada válida se o **par email/senha** corresponder exatamente ao cadastro existente.
- O sistema não deve informar qual campo (email ou senha) está incorreto, para evitar vazamento de informações sobre contas existentes.

---

## 5. Casos de Uso Relacionados

| ID    | Nome            | Descrição Breve                                      |
|-------|-----------------|------------------------------------------------------|
| UC001 | Realizar Login  | Permitir que um usuário acesse o sistema após autenticação. |

---

## 6. Fluxo Básico do Caso de Uso (UC001 - Realizar Login)

1. Usuário acessa a tela de login.
2. Usuário informa email e senha.
3. Clica no botão "Entrar".
4. Sistema valida os dados:
   - Se vazios → exibe mensagem de erro.
   - Se inválidos → exibe mensagem de erro genérica.
   - Se válidos → redireciona para a home.

---

## 7. Mensagens de Erro

| Situação                                     | Mensagem exibida                                 |
|---------------------------------------------|--------------------------------------------------|
| Campos vazios                                | "Usuário e senha precisam ser preenchidos"       |
| Credenciais inválidas ou não cadastradas     | "Usuário e/ou senha inválidos" (sugestão genérica para segurança) |

---

