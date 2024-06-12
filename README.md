#  🚀 Projeto   Viagem 🚗

## Projeto

- API para uma Agência de viágens com três tabelas Destinos[id, cidade, valor, data], Hoteis[id, nome, valor, avaliacao, email, site] e PontosTuristicos[nome, endereco, telefone, valor]



## Iniciar um projeto com Prisma
- 1 Criar uma pasta para o projeto
- 2 Abrir com VsCode
- 3 Abrir um termina **CTRL + "** cmd ou bash e instalar o framework globalmente
```bash
npm i -g prisma
```
- 4 Iniciar o projeto com o ORM Prisma e a biblioteca do SGBD, em nosso casso o MySQL MariaDB
```bash
prisma init --datasource-provider mysql
```
- 5 Editar o arquivo com a **variável de ambiente** com a **string** de conexão com o Banco de dados, quando o App for implantado esta string será alterada com as configuraçõe do servidor SGBD
<br>.env
```js
DATABASE_URL="mysql://root:@localhost:3306/nome_banco_de_dados"
```
- 6 Criar os **Modelos** de tabelas e relacionamentos no arquivo ./prisma/shema.prisma conforme exemplo a seguir<br>shema.prisma
```js


```
- 7 Criar as rotas<br>./src/routes.js
  
```js
const express = require('express');

const router = express.Router();

const clientes = require('./controllers/clientes');
const telefones = require('./controllers/telefones');

router.get('/', (req, res) => {
    res.send('Hello World').end();
});

//Clientes
router.post('/clientes', clientes.create);
router.get('/clientes', clientes.read);
router.delete('/clientes/:id', clientes.remove);
router.put('/clientes/:id', clientes.update);

router.get('/cliente/:id', clientes.readById);
router.post('/clientes/nome', clientes.readByName);


module.exports = router;
```
- 8 editar o server <br>server.js
```js
const express = require('express');
const cors = require('cors');

const app = express();

const router = require('./src/routes');

app.use(express.json());
app.use(cors());
app.use(router);

app.listen(3000, () => {
    console.log("Running on 3000");
});
```
- 9 Executar a API
```bash
nodemon
```
- 10 Testar com **Insomnia**, **Postman** ou outra ferramenta de teste unitário.
