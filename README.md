
# 004 Django 5 - Arquivo .env 

### O que é e para que serve o arquivo .env?

O arquivo .env é um arquivo de texto simples que armazena variáveis de ambiente usadas por uma aplicação para configurar suas operações. Em projetos Django, ele é amplamente utilizado para armazenar informações sensíveis e configurações específicas do ambiente, como a SECRET_KEY, configuração de DEBUG, credenciais de banco de dados, de API's e outras variáveis importantes que não devem ser compartilhadas publicamente.

## COMO RODAR ESSE PROJETO EM SEU COMPUTADOR:

### Requisitos

- **Python 3.12 com PIP e venv**
- **o Django 5 requer Python 3.10 ou superior.**

- **No [repositório 001](https://github.com/Django-Dev-Br/001-django5-basic-project) há explicações sobre PIP e venv**

  [Baixar Python 3.12](https://www.python.org/downloads/release/python-3122/)

  Confira o vídeo para saber como trabalhar com múltiplas versões do Python e com venv (ambiente virtual):  
  [![Watch the video](https://img.youtube.com/vi/eetDeQrv0Rs/0.jpg)](https://youtu.be/eetDeQrv0Rs)


### Passos para Executar

1. **Clone o repositório**:
    ```bash
    git clone https://github.com/Django-Dev-Br/004-django5-dot-env-file.git
  
    ```

2. **Crie um ambiente virtual**:
   
    **Windows**
    ```bash
     python -m venv myvenv  
    ```
   **Linux**
    ```bash
     python3 -m venv myvenv  
    ```

3. **Ative o ambiente virtual criado**:
   
    **Windows**
    ```python
    myvenv\Scripts\activate  
    ```

   **Linux**
    ```python
    source myvenv/bin/activate  
    ```

4. **Instale o Django**:

   Fazer a instalação após a ativação da virtual env fará com que a instalação seja feita nessa pasta ao invés do computador. Isso significa que o pacote Django não estará disponivel para todos os usuários do computador, mas apenas para o contexto no qual essa venv esteja ativada. Veremos sua ativação logo abaixo.

    **Instalação manualmente via gerenciador de dependências PIP**
    ```bash
    pip install django
    ```
    - use, preferencialmente, a versão 5.1. Para tanto, execute o comando:

     ```bash
    pip install  "django>=5.1,<=5.2"
    ```

    ----- **OU** -----

    **Instalação via arquivo requirements**
    ```bash
    pip install -r requirements.txt
    ```
    O arquivo requirements.txt é um arquivo de texto que contém uma lista de pacotes a ser instalado em uma venv. É uma boa prática de programação do ecossistema Python.

    
5. **Instale a Biblioteca Python Dotenv**:

  Este projeto utiliza a biblioteca `python-dotenv` para carregar as configurações do arquivo `.env`. Instale-a com o comando:

  ```bash
  pip install python-dotenv
  ```

6. **Acesse a Pasta do Projeto**:
    ```bash
    cd 004-django5-dot-env-file
    ```

7. **Crie o arquivo `.env` manualmente no diretório root do projeto**:

    **Linux**
    ```python
    touch .env  
    ```
    
    **Windows**
    ```python
    echo. > .env  
    ```
   
8. **Adicione ao .env as configurações variáveis a seguir**:

    Para gerar uma `SECRET_KEY`, execute o seguinte comando no terminal:

    ```bash
    python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
    ```

    Copie e cole a senha gerada no local indicado abaixo no seu arquivo .env:
   
   ```plaintext
    SECRET_KEY=sua_chave_secreta_aqui
    ```

6. **Execute o servidor de desenvolvimento**:
    ```python
    python manage.py runserver
    ```
     Após executar o servidor de desenvolvimento, você pode acessar o Django no seguinte endereço:

      [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/)

### Configurações do settings.py para usar SECRET_KEY do arquivo .env

  Adicione o seguinte código no início do arquivo `settings.py` para carregar a `SECRET_KEY` do arquivo `.env`:
  
  ```python
  import os
  from pathlib import Path
  from dotenv import load_dotenv
  
  # Caminho base do projeto
  BASE_DIR = Path(__file__).resolve().parent.parent
  
  # Carregar variáveis do arquivo .env
  load_dotenv()
  
  # Substitua a linha de código na qual está a SECRET_KEY por esta:
  SECRET_KEY = os.getenv('SECRET_KEY')
  ```

### Estrutura de Diretórios do Projeto

```
004-django5-env-example/
├── .env                  # Arquivo contendo a SECRET_KEY e DEBUG=True
├── .gitignore            # Arquivo que especifica quais arquivos e diretórios o Git deve ignorar
├── myproject/
│   ├── __init__.py       # Marca o diretório como um pacote Python
│   ├── asgi.py           # Configurações para o servidor ASGI (usado para aplicações assíncronas)
│   ├── settings.py       # Configurações do projeto, incluindo uso do arquivo .env
│   ├── urls.py           # Mapeamento de requisições HTTP e redirecionamento para os templates HTML
│   └── wsgi.py           # Configurações para o servidor WSGI (usado para servir a aplicação)
└── manage.py             # CLI do Django, um script de linha de comando para tarefas administrativas do Django
```


### OBS: Como Criar um Projeto Django

Se desejar criar seu próprio projeto Django, use o seguinte comando após criar e ativar a virtual env e instalar o django nela, conforme orientações acima:

```python
django-admin startproject myproject
```

### Sobre Nosso Treinamento Prático-Profissional com projeto real para iniciantes e avançados em web DevOps Full-stack com Python, Django, Bootstrap e Linux.

[Django Developers Brasil - Aprenda programando enquanto programa aprendendo!](https://django.dev.br/)

Nosso treinamento oferece uma experiência prática de aprendizado de programação, adequada tanto para iniciantes quanto para desenvolvedores avançados. Você participará de um projeto real de desenvolvimento de software em um ambiente corporativo autêntico, onde pessoas com diferentes níveis de conhecimento irão colaborar, aprendendo umas com as outras.

**Junte-se a nós!** E desenvolva as habilidades necessárias para o mercado de trabalho, aprimorando tanto seus conhecimentos técnicos quanto suas soft skills em um ambiente colaborativo e realista.
