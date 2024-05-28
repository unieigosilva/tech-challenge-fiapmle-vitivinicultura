
## Visão Geral da EMBRAPA API

### Descrição

Este projeto permite realizar um Web Scrapping no site sobre "Dados da Vitivinicultura" da Embrapa. http://vitibrasil.cnpuv.embrapa.br/
A API permite realizar consultas, fornecendo dados relevantes através de endpoints RESTful. A API utiliza autenticação JWT para segurança.

### Base URL
```
https://127.0.0.0:8000
```

## Autenticação
Esta API usa JWT (JSON Web Tokens) para autenticação. Para acessar os endpoints protegidos, é necessário incluir um token JWT válido no cabeçalho das requisições.

### Obter Token JWT
**Endpoint:** `/token`

**Método:** `POST`

**Parâmetros de Requisição:**
- Não há necessidade de informar usuário e senha para a obtenção do token, apenas o acesso ao Endpoint já é o suficiente para gerar o token desejado.

**Corpo da Requisição:**
```json
{
   
}
```

**Resposta de Sucesso:**
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

**Exemplo de Requisição:**
```bash
curl -X POST "https://127.0.0.0:8000/token" -H "Content-Type: application/json" -d '{}'
```

## Endpoints

### 1. Consultar dados da Embrapa

**Endpoint:** `/embrapa/consulta`

**Método:** `GET`

**Parâmetros de Consulta:**
- `query`: (string) Termo de busca a ser consultado no site da Embrapa.

**Cabeçalhos de Requisição:**
- `Authorization`: (string) Bearer token

**Resposta de Sucesso:**
```json
{
    "resultados": [
        {
            "titulo": "Título do Artigo",
            "link": "https://embrapa.br/link-do-artigo",
            "resumo": "Resumo do artigo."
        }
    ]
}
```

**Exemplo de Requisição:**
```bash
curl -X GET "https://api.exemplo.com/embrapa/consulta?query=agricultura" -H "Authorization: Bearer seu_token_jwt"
```

## Mensagens de Erro

### Erro de Autenticação
**Código:** `401 Unauthorized`

**Resposta:**
```json
{
    "message": "Token JWT inválido ou ausente."
}
```

### Erro de Parâmetros
**Código:** `400 Bad Request`

**Resposta:**
```json
{
    "message": "Parâmetros de consulta inválidos."
}
```

### Erro Interno do Servidor
**Código:** `500 Internal Server Error`

**Resposta:**
```json
{
    "message": "Ocorreu um erro interno no servidor."
}
```

## Plano de Deploy

### Passos para o Deploy
1. **Configurar o Ambiente:**
   - Escolher um provedor de hospedagem (AWS, Heroku, etc.).
   - Configurar o ambiente virtual e instalar dependências.

2. **Implementar o Servidor:**
   - Utilizar um framework como Flask ou FastAPI.
   - Configurar rotas e métodos.

3. **Configurar Autenticação JWT:**
   - Implementar middleware de autenticação.
   - Configurar geração e verificação de tokens.

4. **Testar a API:**
   - Realizar testes unitários e de integração.
   - Validar respostas e erros.

5. **Realizar o Deploy:**
   - Utilizar ferramentas como Docker para containerização.
   - Configurar CI/CD para deploy automático.

6. **Compartilhar o Link:**
   - Disponibilizar o link do ambiente de produção.
   - Criar documentação pública.


