# SRS - Especificação de Requisitos de Software  
## Sistema: BugBank  
**Versão:** 1.0  
**Data:** 03/05/2025  
**Responsável:** Luis Lopes  

---

## 1. Visão Geral  
Este documento descreve os requisitos funcionais e não funcionais do sistema **BugBank**, com foco nos módulos de **Login**, **Cadastro**, **Transferência** e observações sobre **Pagamento**. O objetivo é assegurar que cada funcionalidade atenda aos critérios esperados e forneça uma base clara para os testes.

---

## 2. Requisitos Funcionais  

### 2.1 Módulo: Login  

#### RF001 - Campos obrigatórios  
- O sistema deve exigir o preenchimento dos campos **e-mail** e **senha** para tentar login.  

#### RF002 - Validação de campos vazios  
- Se o usuário tentar realizar login sem preencher um ou ambos os campos obrigatórios, o sistema deve exibir a mensagem:  
  **"Usuário e senha precisam ser preenchidos"**.  

#### RF003 - Validação de credenciais  
- O sistema **não deve permitir** acesso caso o e-mail e/ou senha informados **não correspondam a um usuário previamente cadastrado**.  

#### RF004 - Redirecionamento após login bem-sucedido  
- Se o usuário informar credenciais válidas, o sistema deve redirecioná-lo para a tela **Home** do sistema.  

---

### 2.2 Módulo: Cadastro  

#### RF005 - Campos obrigatórios  
- Os campos **Nome**, **Email**, **Senha** e **Confirmação de Senha** são de preenchimento obrigatório.  

#### RF006 - Validação de campos vazios  
- Nome vazio → **"Nome não pode ser vazio"**  
- Email vazio → **"Email não pode ser vazio"**  
- Senha vazia → **"Senha não pode ser vazio"**  
- Confirmação de senha vazia → **"Confirmar senha não pode ser vazio"**  

#### RF007 - Criação de conta com ou sem saldo  
- Se o usuário marcar a opção **"Criar conta com saldo"**, a conta deve ser criada com **R$ 1.000,00**.  
- Se a opção estiver desmarcada, a conta deve ser criada com **R$ 0,00**.  

#### RF008 - Validação de senhas  
- O sistema deve validar se **senha** e **confirmação de senha** são **iguais**.  

#### RF009 - Confirmação de cadastro  
- Ao cadastrar com sucesso, o sistema deve exibir o **número da conta criada**.  

---

### 2.3 Módulo: Transferência  

#### RF010 - Transferência para contas válidas  
- Somente será permitida transferência para **contas existentes e válidas**.  

#### RF011 - Validação de saldo  
- A transferência só será concluída se o **valor da transação for menor ou igual ao saldo disponível**.  

#### RF012 - Conta inválida  
- Caso a conta de destino seja inválida ou inexistente, exibir:  
  **"Conta inválida ou inexistente"**.  

#### RF013 - Validação de número da conta  
- O campo **número da conta e dígito** deve aceitar apenas **números**.  

#### RF014 - Campo de descrição obrigatório  
- O campo de **descrição da transferência** é de preenchimento obrigatório.  

#### RF015 - Valor inválido  
- O valor da transferência não pode ser **igual ou menor que zero**.  

#### RF016 - Transferência concluída  
- Após uma transferência bem-sucedida, deve:  
  - Debitar o valor da conta origem  
  - Exibir a mensagem: **"Transferência realizada com sucesso"**  
  - Redirecionar o usuário para a tela de **extrato**  

---

### 2.4 Módulo: Pagamento  

> ⚠️ Funcionalidade em desenvolvimento.  

---

## 3. Requisitos Não Funcionais  

### RNF001 - Tempo de resposta  
- A autenticação e transações devem ser processadas em até **2 segundos**.  

### RNF002 - Segurança  
- Todas as informações sensíveis, especialmente **senhas**, devem ser transmitidas via **HTTPS (criptografado)**.  

### RNF003 - Compatibilidade  
- O sistema deve funcionar nos principais navegadores modernos: **Chrome, Firefox, Edge e Safari**.  

---

## 4. Regras de Negócio  

- O sistema **não deve informar qual campo (e-mail ou senha)** está incorreto durante o login.  
- O campo **descrição** na transferência é sempre obrigatório.  
- A conta só é criada se todos os campos obrigatórios forem preenchidos corretamente e as senhas coincidirem.  

---

## 5. Casos de Uso Relacionados  

| ID     | Nome                  | Descrição Breve                                               |
|--------|-----------------------|----------------------------------------------------------------|
| UC001  | Realizar Login         | Permitir que um usuário acesse o sistema após autenticação.   |
| UC002  | Realizar Cadastro      | Permitir que um usuário crie uma nova conta no sistema.       |
| UC003  | Realizar Transferência | Efetuar uma transferência entre contas válidas.               |

---

## 6. Fluxo Básico dos Casos de Uso  

### UC001 - Realizar Login  
1. Usuário acessa a tela de login  
2. Informa e-mail e senha  
3. Clica em "Entrar"  
4. Sistema valida os dados:  
   - Se vazios → exibe mensagem de erro  
   - Se inválidos → exibe mensagem genérica  
   - Se válidos → redireciona para a home  

### UC002 - Realizar Cadastro  
1. Usuário acessa a tela de cadastro  
2. Preenche os campos obrigatórios  
3. Define se quer conta com saldo ou não  
4. Clica em "Cadastrar"  
5. Sistema valida dados:  
   - Campos vazios → exibe mensagens específicas  
   - Senhas diferentes → exibe erro  
   - Dados corretos → cria conta e exibe número  

### UC003 - Realizar Transferência  
1. Usuário logado acessa tela de transferência  
2. Preenche número da conta de destino, valor e descrição  
3. Clica em "Transferir"  
4. Sistema valida dados:  
   - Conta inválida → exibe erro  
   - Saldo insuficiente → exibe erro  
   - Dados válidos → realiza transferência, debita valor e redireciona ao extrato  

---

## 7. Mensagens de Erro  

| Situação                                           | Mensagem exibida                                 |
|---------------------------------------------------|--------------------------------------------------|
| Campos de login vazios                            | "Usuário e senha precisam ser preenchidos"       |
| Credenciais inválidas                              | "Usuário e/ou senha inválidos"                   |
| Nome não preenchido no cadastro                   | "Nome não pode ser vazio"                        |
| Email não preenchido no cadastro                  | "Email não pode ser vazio"                       |
| Senha não preenchida no cadastro                  | "Senha não pode ser vazio"                       |
| Confirmação de senha vazia                        | "Confirmar senha não pode ser vazio"             |
| Conta de destino inválida na transferência        | "Conta inválida ou inexistente"                  |
| Valor da transferência menor ou igual a zero      | "Valor inválido" (mensagem sugerida)             |

---
