# Parte 1 - Cadastro de Usuários
Projeto final para a disciplina de desenvolvimento de Microsserviços e APIs

[Postman Collection para testes](https://github.com/rafael-pa/mba-fiap-apis/blob/master/Projeto%20final%20-%20parte%201.postman_collection.json)

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
