# Comandos mais utilizados no Docker

#### Lista a situação dos containers atuais
```
docker ps -a
```

#### Lista as imagens disponíveis
```
docker images 
```

#### Remove um container
```
docker rm
```

#### Remove uma imagem
```
docker rmi
```

#### Baixa, cria container e executa uma imagem local ou à partir do hub.docker.com
```
docker run -v /var/www:/var/www -p 80:80 vinnyfs89/{image} 
```

#### Inicia um container existente
```
docker start
```

#### Interrompe um container existente
```
docker stop
```

#### Entra em um container
```
docker attach (image_id) --sig-proxy=false
  * CTRL + P + Q = sair do terminal sem derrubar o container
  * docker attach --sig-proxy=true
```

#### Docker-Compose Commands
```
docker-compose up -d --build
docker-compose stop
docker-compose build
```

#### Log do container
```
sudo docker logs -f <CONTAINER_ID>
```

#### Swarm
A swarm is a group of machines that are running Docker and joined into a cluster.

Requirements:

- docker-machine
```
base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo install /tmp/docker-machine /usr/local/bin/docker-machine
```

- docker-machine bash completion (Confirm the version and save scripts to **/etc/bash_completion.d** or /usr/local/etc/bash_completion.d)
```
base=https://raw.githubusercontent.com/docker/machine/v0.16.0
    for i in docker-machine-prompt.bash docker-machine-wrapper.bash docker-machine.bash
    do
      sudo wget "$base/contrib/completion/bash/${i}" -P /etc/bash_completion.d
    done
```

- run the command below in your bash:
```
source /etc/bash_completion.d/docker-machine-prompt.bash
```

- add the line below to your **~/.bashrc**
```
PS1='[\u@\h \W$(__docker_machine_ps1)]\$ '
```

Enable swarm mode:
```
docker swarm init
```

Creating docker virtual machine
```
docker-machine create --driver virtualbox myvm1
docker-machine create --driver virtualbox myvm2
```

List Docker Machines
```
docker-machine ls
```

Access Docker Machines
```
docker-machine ssh myvm1
```

Set Docker Machine as Manager:
```
docker-machine ssh myvm1 "docker swarm init --advertise-addr 192.168.99.100"
```

Output:
```

Swarm initialized: current node (0drnc6ulexaajs20z0cbxgm5u) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-824to0hbb6iepvwlopofkb2wmar3u6n47nu5ny42qpy3z36i2g-c9mbey12q7i20xanm9z749afl 192.168.22.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

```

Join a swarm as worker:

```
docker-machine ssh myvm2 "docker swarm join \
--token SWMTKN-1-824to0hbb6iepvwlopofkb2wmar3u6n47nu5ny42qpy3z36i2g-c9mbey12q7i20xanm9z749afl \
192.168.22.100:2377"
```

Viewing nodes in swarm from manager
```
docker-machine ssh myvm1 "docker node ls"
```

- Guia para iniciantes : [aqui](https://github.com/vinnyfs89/dockerCommands/blob/master/docker-160827013030.pdf) ou diretamente pelo [Slideshare](http://pt.slideshare.net/vinnyfs89/docker-essa-baleia-vai-te-conquistar?qid=aed7b752-f313-4515-badd-f3bf811c8a35&v=&b=&from_search=1)
