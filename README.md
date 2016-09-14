# Comandos mais utilizados no Docker

- docker ps -a - lista a situação dos containers atuais
- docker images - lista as imagens disponíveis
- docker rm - remove um container
- docker rmi - remove uma imagem
- docker run - baixa, cria container e executa uma imagem local ou à partir do hub.docker.com
- docker start - inicia um container existente
- docker stop - para um container existente
- docker attach (image_id) --sig-proxy=false
  * CTRL + P + Q = sair do terminal sem derrubar o container
  * docker attach --sig-proxy=true
- docker-compose up -d --build
- docker-compose stop
- docker-compose build
