# Make Your Burguer 🍔

O "Make Your Burguer" é um projeto que permite aos usuários montar seu próprio hambúrguer personalizado usando uma interface interativa desenvolvida com Vue.js para o frontend. No backend, utilizamos a ferramenta CLI `json-server` para simular uma API e manipular arquivos JSON, fornecendo as informações necessárias para exibir as opções de produtos disponíveis.

## 🚀 Funcionalidades

- **Interface Interativa**: Desenvolvida com Vue.js, permitindo que os usuários escolham entre diferentes tipos de pães, carnes e opcionais para montar seu hambúrguer personalizado.
- **Gerenciamento de Pedidos**: Permite adicionar, atualizar e excluir pedidos.
- **API Simulada**: Utiliza `json-server` para fornecer dados em tempo real e simular uma API RESTful com arquivos JSON.

## 🛠️ Tecnologias Utilizadas

- **Frontend**: [Vue.js](https://vuejs.org/)
- **Backend**: [json-server](https://github.com/typicode/json-server)
- **Manipulação de Dados**: Arquivos JSON

## 📽️ Vídeo de Demonstração

[![Watch the video](https://i.ytimg.com/an_webp/KxD9MLkL2JA/mqdefault_6s.webp?du=3000&sqp=CJDA_bUG&rs=AOn4CLBHXTQZtgPAupH6n-TNJ9K_bzcFTQ)](https://www.youtube.com/watch?v=KxD9MLkL2JA)

## 💻 Configuração e Execução

### Requisitos

- Node.js (versão 14 ou superior)
- npm ou yarn

### Frontend

1. **Clonar o Repositório**

   ```bash
   git clone <URL-DO-REPOSITORIO>
   cd make-your-burguer
   ```

2. **Instalar Dependências**

   ```bash
   npm install
   ```

3. **Executar o Servidor de Desenvolvimento**

   ```bash
   npm run serve
   ```

   O aplicativo estará disponível em [http://localhost:8080](http://localhost:8080).

### Backend

1. **Instalar json-server**

   ```bash
   npm install -g json-server
   ```

2. **Configurar o Servidor**

   No diretório do projeto, crie um arquivo `db.json` com o seguinte conteúdo:

   ```json
   {
     "ingredientes": {
       "paes": [
         {
           "id": 1,
           "tipo": "Italiano Branco"
         },
         {
           "id": 2,
           "tipo": "3 Queijos"
         },
         {
           "id": 3,
           "tipo": "Parmesão e Orégano"
         },
         {
           "id": 4,
           "tipo": "Integral"
         }
       ],
       "carnes": [
         {
           "id": 1,
           "tipo": "Maminha"
         },
         {
           "id": 2,
           "tipo": "Alcatra"
         },
         {
           "id": 3,
           "tipo": "Picanha"
         },
         {
           "id": 4,
           "tipo": "Veggie burger"
         }
       ],
       "opcionais": [
         {
           "id": 1,
           "tipo": "Bacon"
         },
         {
           "id": 2,
           "tipo": "Cheddar"
         },
         {
           "id": 3,
           "tipo": "Salame"
         },
         {
           "id": 4,
           "tipo": "Tomate"
         },
         {
           "id": 5,
           "tipo": "Cebola roxa"
         },
         {
           "id": 6,
           "tipo": "Pepino"
         }
       ]
     },
     "status": [
       {
         "id": "1",
         "tipo": "Solicitado"
       },
       {
         "id": "2",
         "tipo": "Em produção"
       },
       {
         "id": "3",
         "tipo": "Finalizado"
       }
     ],
     "burgers": []
   }
   ```

3. **Configure o comando de execução no arquivo `package.json` no bloco `scripts`**

   ```bash
    "backend": "json-server --watch db/db.json"
   ```

4. **Iniciar o Servidor json-server no Terminal**
   ```bash
   npm run backend
   ```

   O servidor da aplicação está disponível em `http://localhost:8080` e a API encontra-se na rota `http://localhost:3000`.

--- 
<p align="center">2024 - Maria de Fátima Nunes Alves</p>