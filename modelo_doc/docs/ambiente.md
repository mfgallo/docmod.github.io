# Criando Jupyter Notebook com Docker

Utilizando uma imagem já disponível no dockerhub (jupyter/tensorflow-notebook)

```script
docker run jupyter/tensorflow-notebook
```

E depois executar docker run
```script
docker run -p 8888:8888 jupyter/tensorflow-notebook 
```