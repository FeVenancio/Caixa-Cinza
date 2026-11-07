# Testes Caixa Cinza em API de Autenticação com Supabase

## 1. Introdução

Este projeto apresenta a implementação e execução de testes caixa cinza em uma API de autenticação utilizando a plataforma Supabase e a ferramenta Postman Desktop.

A atividade teve como finalidade verificar o funcionamento dos mecanismos de autenticação, analisando requisições HTTP, códigos de resposta, mensagens de erro e validações realizadas pela API.

## 2. Objetivo da Atividade

O objetivo foi desenvolver conhecimentos práticos sobre testes de software, com foco em APIs de autenticação.

Foram realizadas atividades de configuração do ambiente, criação de usuários, elaboração de requisições HTTP e execução de cenários positivos e negativos.

## 3. Configuração do Supabase

Foi criado um projeto na plataforma Supabase com o nome `ProjetoAutenticacao`.

A autenticação por e-mail foi habilitada e um usuário de teste foi cadastrado para permitir a execução dos testes de login.

Também foram obtidas as credenciais necessárias para comunicação com a API:

- Project URL: endereço do projeto.
- Publishable Key: chave pública de acesso à API.

Essas informações foram utilizadas na integração com o Postman.

**Evidências:**

- Projeto criado no Supabase.
- Configuração de autenticação por e-mail.
- Usuário de teste cadastrado.
- Credenciais da API.

## 4. Configuração do Postman

Foi utilizado o Postman Desktop para desenvolver e executar as requisições HTTP.

Foi criado o Workspace `Testes API - Supabase` e um Environment chamado `Supabase - Testes`.

Foram configuradas as seguintes variáveis:

| Variável | Descrição |
|---|---|
| base_url | Endereço da API |
| api_key | Chave pública do Supabase |
| email | E-mail do usuário de teste |
| password | Senha do usuário de teste |

A utilização de variáveis facilitou a organização e reutilização das informações durante os testes.

## 5. Configuração das Requisições

Foi criada uma requisição HTTP utilizando o método POST.

**Endpoint:**

`{{base_url}}/auth/v1/token?grant_type=password`

**Headers utilizados:**

| Header | Valor |
|---|---|
| apikey | {{api_key}} |
| Authorization | Bearer {{api_key}} |
| Content-Type | application/json |

**Body JSON:**

```json
{
  "email": "{{email}}",
  "password": "{{password}}"
}
```

A requisição tem como finalidade realizar a autenticação de um usuário utilizando e-mail e senha.

Quando as credenciais são válidas, a API retorna informações da sessão, incluindo o access token.

## 6. Execução dos Testes

Foram executados cinco cenários para verificar o comportamento da API diante de diferentes entradas.

Os testes foram realizados diretamente pelo Postman Desktop.

### Cenários executados

1. Login válido: utilização de e-mail e senha corretos.
2. Senha incorreta: utilização de e-mail correto e senha inválida.
3. Usuário inexistente: tentativa de autenticação com e-mail não cadastrado.
4. Campos vazios: envio de e-mail e senha vazios.
5. Credenciais inválidas: utilização de e-mail em formato inválido.

Durante a execução foram analisados os códigos HTTP, respostas JSON e mensagens retornadas pela API.

## 7. Resultados Obtidos

A tabela apresenta os resultados observados durante a execução dos testes.

| ID | Cenário | Resultado esperado | Resultado obtido | Status |
|---|---|---|---|---|
| CT01 | Login válido | HTTP 200 e access token | HTTP 200 OK | OK |
| CT02 | Senha incorreta | Erro de autenticação | HTTP 400 | OK |
| CT03 | Usuário inexistente | Acesso negado | HTTP 400 - invalid_credentials | OK |
| CT04 | Campos vazios | Erro de validação | HTTP 400 - validation_failed | OK |
| CT05 | Credenciais inválidas | Erro de autenticação | HTTP 400 - invalid_credentials | OK |

Todos os cenários apresentaram respostas compatíveis com o comportamento esperado da autenticação.

### Evidências

Os prints das requisições e respostas estão armazenados na pasta `prints/`.

A planilha detalhada dos testes está disponível na pasta `planilha/`.

## 8. Registro dos Testes

Os resultados foram documentados em uma planilha contendo:

- Identificação do teste.
- Cenário executado.
- Dados de entrada.
- Resultado esperado.
- Resultado obtido.
- Status.
- Observações.

A documentação permite acompanhar os testes realizados e facilita a identificação de possíveis falhas.

## 9. Conclusão

A atividade permitiu compreender na prática o funcionamento de uma API de autenticação e a importância dos testes caixa cinza no desenvolvimento de software.

Foi possível configurar o Supabase, integrar a plataforma ao Postman e executar cinco cenários diferentes de autenticação.

Os resultados demonstraram que a API conseguiu autenticar corretamente o usuário válido e rejeitar as tentativas com dados incorretos ou incompletos.

Uma melhoria futura seria ampliar os cenários de teste, incluindo validações de segurança, expiração de tokens, recuperação de senha e controle de sessões.

Conclui-se que os testes caixa cinza são importantes porque permitem avaliar o comportamento interno e externo de uma aplicação, contribuindo para a qualidade, confiabilidade e segurança dos sistemas.

---

**Ferramentas utilizadas:**
- Supabase
- Postman Desktop
- GitHub# Caixa-Cinza
