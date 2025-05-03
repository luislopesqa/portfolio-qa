# SRS - Especificação de Requisitos de Software  
## Sistema: BugBank  
**Versão:** 1.0  
**Data:** 03/05/2025  
**Responsável:** Luis Lopes  

---

## 1. Visão Geral  
Este documento especifica os requisitos funcionais e não funcionais do sistema **BugBank**, uma aplicação com o objetivo de simular transações bancárias e oferecer um ambiente de testes intencionalmente com falhas para fins educativos e de QA.  

Os módulos cobertos incluem:  
- Login  
- Cadastro  
- Transferência  
- Pagamento (em desenvolvimento)  
- Extrato  
- Saque (em desenvolvimento)  

---

## 2. Requisitos Funcionais  

### 2.1 Módulo: Login  

#### RF001 - Campos obrigatórios  
- O sistema deve exigir o preenchimento dos campos **e-mail** e **senha** para tentar login.  

#### RF002 - Validação de campos vazios  
- Se o usuário tentar realizar login sem preencher um ou ambos os campos obrigatórios, o sistema deve exibir:  
  **"Usuário e senha precisam ser preenchidos"**.  

#### RF003 - Validação de credenciais  
- O sistema **não deve permitir acesso** caso o e-mail e/ou senha não correspondam a um usuário previamente cadastrado.  

#### RF004 - Redirecionamento após login bem-sucedido  
- Com credenciais válidas, o usuário deve ser redirecionado para a tela **Home**.  

---

### 2.2 Módulo: Cadastro  

#### RF005 - Campos obrigatórios  
- Os campos **Nome**, **Email**, **Senha** e **Confirmação de senha** são obrigatórios.  

#### RF006 - Validações individuais  
- Nome vazio: "Nome não pode ser vazio"  
- Email vazio: "Email não pode ser vazio"  
- Senha vazia: "Senha não pode ser vazio"  
- Confirmação vazia: "Confirmar senha não pode ser vazio"  

#### RF007 - Saldo inicial  
- Com a opção "Criar conta com saldo" **ativa**, a conta é criada com **R$ 1.000,00**.  
- Com a opção **inativa**, a conta é criada com **R$ 0,00**.  

#### RF008 - Senhas iguais  
- As senhas e a confirmação devem **obrigatoriamente coincidir**.  

#### RF009 - Confirmação de criação  
- Após cadastro com sucesso, deve ser exibido o **número da conta criada**.  

---

### 2.3 Módulo: Transferência  

#### RF010 - Contas válidas  
- Só é permitida a transferência para **contas válidas e existentes**.  

#### RF011 - Verificação de saldo  
- A transferência só é possível se o **saldo for igual ou superior ao valor transferido**.  

#### RF012 - Conta inválida  
- Transferência para conta inexistente deve exibir:  
  **"Conta inválida ou inexistente"**.  

#### RF013 - Validações adicionais  
- Número e dígito da conta devem aceitar **somente números**.  
- Campo **descrição** é obrigatório.  
- Valor da transferência deve ser **maior que zero**.  

#### RF014 - Transferência bem-sucedida  
- O valor deve ser debitado e a mensagem exibida:  
  **"Transferência realizada com sucesso"**.  
- Usuário deve ser redirecionado automaticamente para o **extrato**.  

---

### 2.4 Módulo: Pagamento  

> ⚠️ Funcionalidade em desenvolvimento.  

---

### 2.5 Módulo: Extrato  

#### RF017 - Exibição de saldo  
- O extrato deve mostrar o **saldo atual disponível** na conta.  

#### RF018 - Exibição de transações  
- Cada transação deve exibir:  
  - **Data da transação**  
  - **Tipo**: Abertura de conta / Transferência enviada / Transferência recebida  

#### RF019 - Cores e sinais  
- Valores de **saída**: em **vermelho** com prefixo **"-"**.  
- Valores de **entrada**: em **verde**.  

#### RF020 - Transações sem comentário  
- Devem exibir o símbolo: **"(-)"**.  

---

### 2.6 Módulo: Saque  

> ⚠️ Funcionalidade em desenvolvimento.  

---

## 3. Requisitos Não Funcionais  

### RNF001 - Tempo de resposta  
- A autenticação deve ocorrer em até **2 segundos** após o envio das credenciais.  

### RNF002 - Segurança  
- As senhas devem ser transmitidas via **HTTPS**, garantindo **criptografia**.  

### RNF003 - Compatibilidade  
- O sistema deve funcionar em navegadores modernos:  
  - **Google Chrome**  
  - **Mozilla Firefox**  
  - **Microsoft Edge**  
  - **Safari**  

---

## 4. Regras de Negócio  

- A autenticação é válida apenas se o **par e-mail/senha** corresponder exatamente ao cadastro existente.  
- O sistema **não deve indicar qual campo está incorreto** (e-mail ou senha), para evitar vazamento de informações.  

---

## 5. Casos de Uso Relacionados  

| ID    | Nome                   | Descrição                                             |
|-------|------------------------|--------------------------------------------------------|
| UC001 | Realizar Login         | Permitir que um usuário acesse o sistema.             |
| UC002 | Realizar Cadastro      | Criar uma nova conta bancária.                        |
| UC003 | Realizar Transferência | Efetuar uma transferência entre contas existentes.    |
| UC004 | Visualizar Extrato     | Visualizar o histórico de transações da conta.        |
| UC005 | Realizar Saque         | (Em desenvolvimento) Permitir saques bancários.       |

---

## 6. Fluxos Básicos dos Casos de Uso  

### UC001 - Realizar Login  
1. Usuário acessa a tela de login.  
2. Preenche e-mail e senha.  
3. Clica em "Entrar".  
4. Sistema valida os dados:  
   - Vazios: exibe erro.  
   - Inválidos: exibe erro genérico.  
   - Válidos: redireciona para a Home.  

### UC002 - Realizar Cadastro  
1. Usuário acessa a tela de cadastro.  
2. Preenche os campos obrigatórios.  
3. Escolhe se quer criar conta com saldo.  
4. Informa senhas idênticas.  
5. Clica em "Cadastrar".  
6. Se tudo estiver correto, a conta é criada com saldo definido, e o número da conta é exibido.  

### UC003 - Realizar Transferência  
1. Usuário acessa a tela de transferência.  
2. Preenche número, dígito, valor e descrição.  
3. Clica em "Transferir".  
4. Sistema valida as informações:  
   - Conta inválida: exibe erro.  
   - Valor inválido ou saldo insuficiente: exibe erro.  
   - Dados válidos: realiza a transferência, debita o valor, mostra mensagem de sucesso e redireciona para o extrato.  

### UC004 - Visualizar Extrato  
1. Usuário acessa o extrato.  
2. Sistema exibe saldo atual e lista de transações com:  
   - Data  
   - Tipo  
   - Valor (com sinal e cor)  
   - Descrição ou "(-)"  

### UC005 - Realizar Saque  
> ⚠️ Em desenvolvimento.  

---

## 7. Mensagens de Erro  

| Situação                                     | Mensagem exibida                                 |
|---------------------------------------------|--------------------------------------------------|
| Campos de login vazios                      | "Usuário e senha precisam ser preenchidos"       |
| Credenciais inválidas                       | "Usuário e/ou senha inválidos"                   |
| Nome em branco no cadastro                  | "Nome não pode ser vazio"                        |
| Email em branco no cadastro                 | "Email não pode ser vazio"                       |
| Senha em branco no cadastro                 | "Senha não pode ser vazio"                       |
| Confirmação em branco no cadastro           | "Confirmar senha não pode ser vazio"             |
| Conta inválida na transferência             | "Conta inválida ou inexistente"                  |
| Valor de transferência zero ou negativo     | "Valor inválido para transferência" *(sugestão)* |

---
