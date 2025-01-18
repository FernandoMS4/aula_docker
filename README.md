# Aula de Docker


# **1: O Docker***
O docker basicamente é a ferramenta que mitiga o "[...]Na minha máquina funciona"

# 2: **Como utilizar o docker***

## **Criação do .dockerignore***

A criação do dockerignore é crucial para excluirmos os arquivos que, são de segurança ou possam deixar a imagem pesada. 

Basicamente é o mesmo arquivo .gitignore

## **Criação do Dockerfile***

Para criarmos o dockerfile é necessário que o arquivo tenha exatamente este nome: Dockerfile

O file segue uma estrutura basica na seguinte ordem:

```
Para definir a versão do python a ser instalada
FROM python: 3.x 
```

```
Para instalação do poetry para controle do ambiente 
RUN pip install poetry
```

```
Para que a máquina possua uma pasta chamada src e aloque o projeto dentro dela
COPY . /src
```

```
Para mover para o diretorio
WORKDIR /src
```

```
Para instalação de todas as dependencias do projeto
RUN poetry install --no-root
```

```
Porta(s) a ser definida para suportar o projeto
EXPOSE 8501
```

```
Linha de comando a ser executada
ENTRYPOINT [ "poetry", "run", "streamlit", "run", "src/front/app.py", "--server.port=8501", "--server.address=0.0.0.0" ]
```
```
Para verificar se a porta está sendo usada:
netstat -ano | findstr :8501
```

```
Para "dezipar" a imagem:
docker run -d -p 8501:8501 --name my-first-container minha-primeira-imagem
```

# **O "Dezipar" a imagem:***
Serve basicamente para criar o container que vai suportar o projeto no docker