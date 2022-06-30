<h1 align="center"> json-server-base-luccas </h1>

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do M3.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login. Além deles, temos 2 endpoints para Esportes e outros 2 endopoints para Senhas.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

```json
{
  "email": "kenzinho@kenzie.com",
  "password": "@12Patinhos",
  "name": "kenzinho",
  "age": 27
}
```

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

```json
{
  "email": "kenzinho@kenzie.com",
  "password": "@12Patinhos"
}
```

### Esportes

<h1 align ='center'> Adicionar Esporte </h1>

Essa rota necessita que o usuário esteja logado para adicionar um novo esporte do qual pratica, portanto deve ser informado no cabeçalho da requisição o campo "Authorization", como também o id no usuário em questão, com "userId".

> Authorization: Bearer {token}

POST /sports

```json
{
  "name": "basquete",
  "practiceTime": "6 years",
  "userId": 1
}
```

<h1 align ='center'> Listar esportes </h1>

Essa rota possibilita a visualização de todos os esportes praticados por todos os usuários, não necessita estar logado.

> GET /sports - FORMATO DA RESPOSTA - STATUS 200

```json
[
  {
    "name": "basquete",
    "practiceTime": "6 years",
    "userId": 1,
    "id": 1
  },
  {
    "name": "futebol",
    "practiceTime": "16 years",
    "userId": 1,
    "id": 2
  },
  {
    "name": "futebol",
    "practiceTime": "20 years",
    "userId": 2,
    "id": 4
  }
]
```

### Senhas

<h1 align ='center'> Adicionar Senha </h1>

Essa rota necessita que o usuário esteja logado para adicionar uma nova senha de alguma plataforma que o mesmo utiliza, portanto deve ser informado no cabeçalho da requisição o campo "Authorization", como também o id no usuário em questão, com "userId".

> Authorization: Bearer {token}

POST /passwords

```json
{
  "plataform": "instagram",
  "password": "kenzinhoinsta123",
  "userId": 1
}
```

<h1 align ='center'> Listar Senhas </h1>

Essa rota necessita que o usuário esteja logado para visualizar e para que os usuários consigam acessar apenas as suas proprias senhas é necessario passar um query params com userId correto, como "/passwords?userId=1".

GET /passwords?userId={id do usuário logado}

> Authorization: Bearer {token}

> GET /passwords?userId=1 - FORMATO DE RESPOSTA - STATUS 200

```json
[
	{
		"plataform": "facebook",
		"password": "kenzinhoface123",
		"userId": 1,
		"id": 4
	},
	{
		"plataform": "cartola FC",
		"password": "kenzinhocartola123",
		"userId": 1,
		"id": 5
	}
]
```
