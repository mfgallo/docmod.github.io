# Criando Jupyter Notebook com Docker

Criando DockerFile

```DockerFile
FROM ubuntu:latest
RUN apt-get update && \
    apt-get install -y python3.9 \
    python3-pip
            
RUN pip3 install JPype1 jupyter pandas numpy seaborn scipy matplotlib pyNetLogo SALib 
    
RUN useradd -ms /bin/bash jupyter
USER jupyter
WORKDIR home/jupyter 
EXPOSE 8888                                           
ENTRYPOINT ["jupyter", "notebook","--allow-root","--ip=0.0.0.0","--port=8888","--no-browser"]
```

Procurando versão miniconda3

```shell
docker search miniconda3
```

Rodando versão mais atualizada

```shell
docker run -i -t --rm --name condaenv -p  8888:8888 continuumio/miniconda3 /bin/bash
```

Dentro do terminal do container roda os comandos abaixo:

```shell
conda update conda
conda install python=3.9.6
conda install -c conda-forge jpype1
conda install jupyter pandas numpy  
pip install SALib seaborn
```

Criando Jupyter Notebook

```shell
mkdir -p /opt/notebooks 
jupyter notebook --notebook-dir=/opt/notebooks --ip='*' --port=8888  --no-browser --allow-root
```