# Plano de Testes – Módulo: Login  
**Sistema:** BugBank  
**Versão:** 1.0  
**Data de criação:** 03/05/2025  
**Elaborado por:** Luis Lopes 

---

## 1. Objetivo
Este plano de testes tem como objetivo definir a estratégia de teste aplicada à funcionalidade de **login** do sistema BugBank, garantindo que o comportamento implementado esteja de acordo com os requisitos definidos.

---

## 2. Escopo

### 2.1 Itens a serem testados
- Validação de campos obrigatórios
- Mensagens de erro para campos vazios
- Tentativa de login com credenciais inválidas
- Login com credenciais válidas
- Redirecionamento para home após login com sucesso

### 2.2 Itens fora de escopo
- Funcionalidade de **cadastro**
- Funcionalidades **pós-login** (como extrato, transferências)
- Testes de segurança como brute force ou SQL Injection (fora do escopo funcional)

---

## 3. Estratégia de Testes

### 3.1 Tipos de Teste
- Teste Funcional
- Teste de Validação de Campos
- Teste de Fluxo Positivo e Negativo

### 3.2 Abordagem
- Testes **manuais** baseados em casos de teste derivados do documento de requisitos
- Execução em navegadores modernos (Chrome, Firefox)

---

## 4. Critérios de Aceitação

| Critério                              | Descrição                                                                 |
|--------------------------------------|---------------------------------------------------------------------------|
| Passar em todos os testes críticos   | Todos os casos de teste do login devem passar sem falhas.                |
| Validação de mensagens               | Mensagens de erro devem seguir os textos definidos no requisito.         |
| Redirecionamento correto             | Usuário deve ser direcionado à home ao autenticar com sucesso.           |

---

## 5. Ambiente de Testes

- **URL de Teste:** https://bugbank.netlify.app/  
- **Navegadores:** Google Chrome, Mozilla Firefox  
- **Dispositivo:** Desktop  
- **Ambiente:** Em nuvem, sem persistência (dados em memória local)

---

## 6. Recursos

- 1 Analista de Testes manual
- Ferramenta de registro de testes: Planilha, TestLink ou TestRail (a definir)
- Ferramenta de reporte de bugs: GitHub Issues ou Jira

---

## 7. Riscos

| Risco                              | Impacto                             | Mitigação                            |
|-----------------------------------|-------------------------------------|--------------------------------------|
| Alterações constantes no sistema  | Pode invalidar os testes            | Validar requisitos antes de testar   |
| Falta de dados persistidos        | Dados são apagados ao recarregar    | Usar testes rápidos com dados novos  |

---

## 8. Cronograma Estimado

| Atividade                | Data Início | Data Fim   |
|--------------------------|-------------|------------|
| Análise de Requisitos    | 03/05/2025  | 03/05/2025 |
| Criação dos Casos de Teste | 03/05/2025  | 04/05/2025 |
| Execução dos Testes      | 04/05/2025  | 05/05/2025 |
| Reporte de bugs e validação final | 05/05/2025 | 06/05/2025 |

---

## 9. Aprovação

| Nome             | Cargo                  | Data        | Assinatura  |
|------------------|------------------------|-------------|-------------|
| Luis Lopes  | Analista de Testes     | 03/05/2025  |

