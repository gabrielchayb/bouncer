Passo 1: Criar o projeto no github com o .gitignore template PYTHON! 
Passo 2: Adicionar 4 arquivos na raiz do projeto: 
- Dockerfile
- .dockerignore 
- .gitignore (adicionar NO FINAL DO ARQUIVO /static, pular uma linha, /data)
- requirements.txt
Passo 3: Criar a configuração do Docker-Compose
- docker-compose.yml 
Passo 4: Adicione a pasta app na raiz do projeto 
- raiz do projeto: pasta app
Passo 5: Vamos construir nossa imagem docker digitando no terminal: docker-compose build
- Building 20.8s (12/12) FINISHED 
Passo 6: Vamos commitar nosso ambiente docker! 
Passo 7: vamos criar nosso django project: docker-compose run --rm app sh -c "django-admin startproject app ." 
-  ✔ Network bouncer_default  Created  
- Dentro da pasta app, deve aparecer varios arquivos, como o settings.py, urls.py, wsgi.py, manage.py, asgi.py. 
Passo 8: vamos dar run no novo serviço para mapear as portas e testar nosso app django: docker-compose up
- November 01, 2024 - 13:52:22
app-1  | Django version 3.2.25, using settings 'app.settings'
app-1  | Starting development server at http://0.0.0.0:8000/ 
app-1  | Quit the server with CONTROL-C.
- http://127.0.0.1:8000/ - aqui deve aparecer o foguetinho do django 
Passo 9: vamos comitar nosso django project criado com sucesso! 
Passo 10: vamos criar nosso django app: docker-compose run --rm app sh -c "python manage.py startapp bouncer"
Passo 11: enable o app bouncer no seu settings.py em INSTALLED APPS: 'bouncer'
Passo 12: mude, em settings.py, ALLOWED HOSTS para ALLOWED_HOSTS = ['*'] (apenas utilizando google app engine para deploy)
Passo 13: fiz outras mudanças em settings.py, é so copiar e colar.
Passo 14: criar uma view: dentro de bouncer, criar uma pasta chamada static, e dentro da pasta static, crie um arquivo chamado style.css
- adicione css styles ali 
Passo 15: criar uma view: dentro de bouncer, criar uma pasta chamada templates, e dentro da pasta templates, criar uma pasta chamada bouncer, e dentro dela um arquivo chamado index.html
- adicione o codigo html 

