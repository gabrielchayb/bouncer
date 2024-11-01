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
- - http://127.0.0.1:8000/ - aqui deve aparecer as mudanças que voce fez

DEPLOY TO GAE

Passo 1: criar docker-compose-deploy, e depois disso, rodar: docker-compose -f docker-compose-deploy.yml run --rm gcloud gcloud --version 
-  ✔ Volume "bouncer_gcp-creds"  Created                                                                                                                              0.0s 
[+] Running 7/7
 ✔ gcloud Pulled                                                                                                                                                   22.9s 
   ✔ 69692152171a Pull complete                                                                                                                                     2.4s 
   ✔ 6f098e2b432d Pull complete                                                                                                                                     2.6s 
   ✔ 01880c0d39a7 Pull complete                                                                                                                                     2.6s 
   ✔ a9be61ca99d9 Pull complete                                                                                                                                     2.6s 
   ✔ 146dff0925e7 Pull complete                                                                                                                                    18.6s 
   ✔ fcad230120c2 Pull complete                                                                                                                                    18.6s 
Google Cloud SDK 341.0.0
alpha 2021.05.14
beta 2021.05.14
bq 2.0.68
core 2021.05.14
gsutil 4.62

Passo 2: crie o app.yaml e não se esqueça de tirar o DEBUG do docker-compose.yml e do settings.py

ENTRE EM: cloud.google.com 
Clique em console
Clique em "novo projeto" 
No canto superior esquerdo da pagina, tenha certeza que seu projeto esta selecionado
No menu esquerdo da pagina, dentro do seu projeto, clique em App Engine: https://console.cloud.google.com/appengine/start?project=bouncer-demo-440414
Crie um projeto e escolha uma região proxima a vc 

