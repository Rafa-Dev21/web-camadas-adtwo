# web-camadas-adtwo

# ADO 2 - Hospedagem da API REST Node.js

Disciplina: Aplicações Web em Camadas  
Aluno: Rafael Oliveira

---

# Objetivo da atividade

O objetivo desta atividade foi hospedar a API REST desenvolvida no projeto final em uma plataforma online, permitindo que a aplicação funcionasse fora da máquina local. Também foi necessário compreender como funcionam as variáveis de ambiente em produção e como a API hospedada se conecta ao banco de dados remoto.

---

# 1. API rodando localmente

## Inicialização do servidor

Durante o desenvolvimento da API utilizei Node.js junto com Express para criação das rotas da aplicação. Para facilitar o desenvolvimento utilizei o nodemon, permitindo reiniciar o servidor automaticamente sempre que ocorria alguma alteração no código.

Comando utilizado durante o desenvolvimento:

```bash
npm run dev
```

Também configurei o script de produção utilizado pela hospedagem:

```bash
npm start
```

---

## Variáveis de ambiente locais

As informações sensíveis da aplicação foram armazenadas no arquivo `.env`.

Estrutura utilizada:

```env
DATABASE_URL=
JWT_SECRET=
```

A variável `DATABASE_URL` foi utilizada para conectar a API ao banco MySQL hospedado no Railway. Já a variável `JWT_SECRET` foi utilizada para autenticação e geração de tokens JWT.

---

## API executando localmente

<img width="937" height="461" alt="image" src="https://github.com/user-attachments/assets/b00e82f8-b94d-4a00-bea0-226ae44b9f37" />

---

# 2. Plataformas gratuitas pesquisadas

## Render

O Render é uma plataforma de hospedagem que suporta aplicações Node.js com Express. A plataforma permite integração direta com GitHub e deploy automático após cada push realizado no repositório.

No plano gratuito existem limitações de recursos e a aplicação pode entrar em modo sleep após um período sem utilização.

Escolhi utilizar o Render porque possui configuração simples, integração fácil com GitHub e deploy rápido.

<img width="1877" height="963" alt="image" src="https://github.com/user-attachments/assets/c82d2ae0-e8df-45ef-87a0-66e133d801e0" />

---

## Railway

O Railway também suporta aplicações Node.js e bancos de dados MySQL. A plataforma possui integração simples com GitHub e configuração prática de variáveis de ambiente.

O plano gratuito possui limite de uso mensal e algumas limitações de recursos computacionais.

Utilizei o Railway para hospedar o banco de dados MySQL da aplicação.

<img width="1893" height="963" alt="image" src="https://github.com/user-attachments/assets/53d4088d-7a29-484c-9c6e-d2eb703d387c" />

---

## Fly.io

O Fly.io permite hospedar aplicações Node.js utilizando containers e deploy por linha de comando.

Apesar de possuir plano gratuito, considerei a configuração mais complexa em comparação ao Render.

Por esse motivo optei por utilizar o Render na hospedagem final da API, até por que foi o que o professor me ensinou utilizar em sala
de aula, então já tinha mais familiaridade.

---

# 3. Deploy da API

## Integração com GitHub

Primeiramente subi os arquivos da API para um repositório público no GitHub.

Depois conectei o repositório ao Render utilizando a opção “New Web Service”. O Render realizou automaticamente o clone do repositório e iniciou o processo de deploy da aplicação.

<img width="1810" height="944" alt="image" src="https://github.com/user-attachments/assets/e3d51ab4-bae4-4232-890b-3ec0a896e1b0" />

<img width="1691" height="812" alt="image" src="https://github.com/user-attachments/assets/d77d2013-a882-4ce6-bc2d-f93a36dba360" />


---

## Variáveis de ambiente

No painel do Render configurei as variáveis de ambiente necessárias para execução da API.

Variáveis utilizadas:

- DATABASE_URL
- JWT_SECRET

Essas variáveis foram adicionadas diretamente no painel da plataforma.

<img width="1885" height="933" alt="image" src="https://github.com/user-attachments/assets/c606e71d-81ee-4f52-b4c3-26ee8662dcde" />

---

## Script de inicialização

No arquivo `package.json` configurei o seguinte script:

```json
"start": "node src/server.js"
```

Esse comando foi utilizado pelo Render para iniciar automaticamente o servidor em produção.

O comando configurado no painel do Render foi:

```bash
npm start
```

---

## Deploy concluído

URL pública da API:

https://api-rifas-i7qy.onrender.com/

Após finalizar todas as configurações o Render realizou o deploy da API com sucesso e gerou uma URL pública para acesso da aplicação.

<img width="1511" height="740" alt="image" src="https://github.com/user-attachments/assets/64efaa27-dbd8-441b-9285-4a2a324d2152" />

---

## Teste da API hospedada

Após o deploy realizei testes utilizando navegador e Insomnia para verificar o funcionamento das rotas da API.

<img width="986" height="708" alt="image" src="https://github.com/user-attachments/assets/8b87a058-9fef-41d7-9313-fe5957c30496" />

---

# 4. Conexão da API com o banco hospedado

A API hospedada no Render continua conectada ao banco MySQL hospedado no Railway através da variável `DATABASE_URL`.

Essa variável contém as informações necessárias para conexão com o banco de dados:

- usuário
- senha
- host
- porta
- nome do banco

As variáveis configuradas diretamente no painel do Render substituem o arquivo `.env` local da máquina durante a execução da aplicação em produção.

Caso o `DATABASE_URL` estivesse incorreto, a API não conseguiria se conectar ao banco de dados. Nesse caso as rotas retornariam erro interno e o Prisma apresentaria erro de conexão.

---

# 5. Problemas encontrados

Durante o processo de deploy encontrei alguns problemas relacionados ao GitHub e à configuração da hospedagem.

Um dos erros ocorreu durante o push para o repositório remoto, pois o repositório já possuía um README e aconteceu conflito de merge no arquivo `package.json`.

Também precisei configurar corretamente o script `start` no `package.json` para que o Render conseguisse iniciar o servidor corretamente.

Outro ajuste necessário foi configurar corretamente as variáveis de ambiente no Render para permitir a conexão da API com o banco hospedado no Railway.

Após corrigir esses problemas o deploy foi concluído com sucesso.

<img width="865" height="191" alt="image" src="https://github.com/user-attachments/assets/d1451390-f8df-4252-96f8-158a992fd146" />

---

# 6. Conclusão

A atividade permitiu compreender melhor como funciona a hospedagem de APIs Node.js em ambiente de produção utilizando plataformas gratuitas.

Também foi possível entender o funcionamento das variáveis de ambiente em produção, deploy automático utilizando GitHub e conexão da API com banco de dados remoto hospedado online.

O processo contribuiu para aprofundar os conhecimentos sobre aplicações web em camadas e funcionamento de APIs em produção.
