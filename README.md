Para realizar esse desafio, vamos seguir as etapas propostas de configuração, criação e teste, e distribuição do contêiner para a aplicação de conversão de distâncias.

# Passo 1: Configuração do Ambiente

## 1. Fork do Repositório e Clonagem:

- Primeiro, faça o fork do repositório https://github.com/jmarcelotse/devops4cloud para sua conta no GitHub.
- Após o fork, clone o repositório em sua máquina local:

bash
```
git clone https://github.com/jmarcelotse/devops4cloud.git
cd devops4cloud
```
## 2. Criação do Dockerfile:

- Dentro do diretório do projeto, crie um arquivo chamado `Dockerfile`. Esse arquivo será utilizado para definir a imagem Docker para a aplicação de conversão de distância em Python.
- O `Dockerfile` deve conter as seguintes instruçõe

dockerfile
```
# Base Image
FROM python:3.13.0

# Define o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copia os arquivos de requisitos e instala as dependências
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copia todo o conteúdo da aplicação para o diretório de trabalho no contêiner
COPY . /app/

# Define a porta que será exposta pelo contêiner
EXPOSE 5000

# Define o comando para iniciar a aplicação
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]
```
- Nesse `Dockerfile`:

 - Utilizamos a imagem base `python:3.13.0` para um ambiente leve e eficiente.
 - Definimos `/app` como diretório de trabalho e copiamos os arquivos necessários.
 - Instalamos as dependências listadas em `requirements.txt` para garantir que a aplicação funcione corretamente.
 - Exponhamos a porta `5000`, que será utilizada pela aplicação.

# Passo 2: Criação e Teste do Contêiner
## 1. Gerar a Imagem Docker:
- Com o `Dockerfile` configurado, gere a imagem Docker:

bash
```
docker build -t jmarcelotse/conversao-distancia:v1 -f Dockerfile .
```
## 2. Executar o Contêiner:

- Execute o contêiner para verificar a aplicação:

bash
```
docker container run -d -p 8282:5000 jmarcelotse/conversao-distancia:v1
```
- A aplicação deve estar acessível em http://localhost:8282.

## 3. Testar a Aplicação:

- Abra o navegador ou use `curl` para fazer requisições e testar a funcionalidade de conversão:
-
bash
```
curl http://localhost:8282/convert?from=meters&to=kilometers&value=1000
```
- Esse teste verifica se o serviço está funcional e respondendo corretamente às requisições de conversão.

## 4. Publicar a Imagem no Docker Hub:
- Faça o push da imagem para o Docker Hub:

bash
```
docker push jmarcelotse/conversao-distancia:v1
```
# Passo 3: Distribuição do Contêiner
## 1. Login no Docker Hub:
- Caso ainda não tenha feito login, entre com suas credenciais do Docker Hub:
bash
```
docker login
```
## 2. Publicar a Imagem no Docker Hub:

- Faça o push da imagem para o Docker Hub:

bash
```
docker tag jmarcelotse/conversao-distancia:v1 jmarcelotse/conversao-distancia:latest
docker push jmarcelotse/conversao-distancia:latest
docker image ls
```
## 3. Enviar o Repositório para Verificação:

- Após publicar a imagem, atualize o README do seu repositório com instruções de como executar a aplicação com Docker, incluindo o comando de pull da imagem no Docker Hub:

markdown
```
### Como executar a aplicação de Conversão de Distâncias

1. Baixe a imagem do Docker Hub:
   bash
   docker pull jmarcelotse/conversao-distancia:latest

```
### 2. Execute o contêiner:

bash
```
docker container run -d -p 8282:5000 jmarcelotse/conversao-distancia:v1
```
### 3. Acesse a aplicação em http://localhost:8282.

Done 2 Testando