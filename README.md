# mba-fiap-apis
Projeto final para a disciplina de desenvolvimento de Microsserviços e APIs

## Parte 1 - Cadastro de Usuários

### /api/usuarios (GET)
- Retorno: lista de usuários cadastrados
```json
{
    "output": "ok",
    "payload": [
        {
            "_id": "<id>",
            "nomeusuario": "teste",
            "email": "testel@teste.com.br",
            "senha": "<hash>",
            "nomecompleto": "Teste do Testador",
            "telefone": "9999999999",
            "datacadastro": "2022-11-02T03:02:05.198Z",
            "__v": 0
        }
    ]
}
```

### /api/usuarios/cadastro (POST)
- Entrada: dados do usuário (todos são obrigatórios)
```json
{
    "nomeusuario": "teste",
    "email": "teste@teste.com.br",
    "nomecompleto": "Teste do testador",
    "telefone": "9999999999",    
    "senha": "123456"
}
```
- Retorno: dados do usuário
```json
{
    "output": "ok",
    "payload": [
        {
            "_id": "<id>",
            "nomeusuario": "teste",
            "email": "testel@teste.com.br",
            "senha": "<hash>",
            "nomecompleto": "Teste do Testador",
            "telefone": "9999999999",
            "datacadastro": "2022-11-02T03:02:05.198Z",
            "__v": 0
        }
    ]
}
```

### /api/usuarios/login (POST)
- Entrada: dados de login
```json
{
    "nomeusuario": "teste",
    "senha": "123456"
}
```
- Retorno: dados de autenticação
```json
{
    "output": "Autenticado",
    "idusuario": "6361ddad13a1e43373041bca",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjYzNjFkZGFkMTNhMWU0MzM3MzA0MWJjYSIsImVtYWlsIjoicmFmYWVsQHRlc3RlLmNvbS5iciIsImlhdCI6MTY2NzM1OTY0MSwiZXhwIjoxNjY3NDQ2MDQxfQ.VjfFAQ94OEg8TzXUVoWreI33L-_U4x6hh65lJp1W5d4"
}
```

### /api/usuarios/atualizar-senha (PUT)
- Entrada: senha (será atualizada para o usuário logado - necessário token no cabeçalho da requisição)
```json
{
    "senha": "123456"
}
```
- Retorno:
```json
{
    "output": "Senha atualizada!",
    "payload": {
        "_id": "<id>",
        "nomeusuario": "teste",
        "email": "teste@teste.com.br",
        "senha": "<hash>",
        "nomecompleto": "Teste do Testador",
        "telefone": "9999999999",
        "datacadastro": "2022-11-02T03:02:05.198Z",
        "__v": 0
    }
}
```

------------

## Parte 2 - Cadastro de Informações Financeiras
### Para acesso a estes endpoints é necessário o token gerado no login da api usuarios no header da requisição ("token")


### /api/financeiro (GET)
- Retorno: lista de informações financeiras cadastradas
```json
{
    "output": "ok",
    "payload": [
        {
            "_id": "6365a6c0d7faaf8ea7394b59",
            "nome_titular": "Teste do Testador",
            "nome_banco": "Banco do Teste",
            "tipo_conta": "Corrente",
            "limite_cartao": 999.99,
            "__v": 0
        }
    ]
}
```

### /api/financeiro/cadastro (POST)
- Entrada: dados financeiros (todos são obrigatórios)
```json
{
    "nome_titular": "Teste do Testador",
    "nome_banco": "Banco do Teste",
    "tipo_conta": "Corrente",
    "limite_cartao": 999.99
}
```
- Retorno: dados financeiros
```json
{
    "output": "ok",
    "payload": [
        {
            "_id": "6365a6c0d7faaf8ea7394b59",
            "nome_titular": "Teste do Testador",
            "nome_banco": "Banco do Teste",
            "tipo_conta": "Corrente",
            "limite_cartao": 999.99,
            "__v": 0
        }
    ]
}
```

### /api/financeiro/atualizar/<id do registro> (PUT)
- Entrada: dados a serem atualizados 
```json
{
    "tipo_conta": "Poupança"
}
```
- Retorno:
```json
{
    "output": "Senha atualizada!",
    "payload": {
        "_id": "63659e74a394c4870f8a19e9",
        "nome_titular": "Rafael Andrade",
        "nome_banco": "Banco do Brasil",
        "tipo_conta": "Poupança",
        "limite_cartao": 1532.49,
        "__v": 0
    }
}
```

### /api/financeiro/apagar/<id do registro> (PUT)
#### Sem dados de entrada e saída
