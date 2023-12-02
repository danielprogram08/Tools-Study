# O que é Docker?

_Existem diversas definições para Docker. Em poucas palavras docker é uma tecnologia capaz de empacotar uma aplicação e executar._

_Você deve esta se perguntando, como assim empacotar? O que são containers? Não se preocupe iremos falar sobre isso a seguir._

_Docker é uma plataforma aberta capaz de empacotar uma aplicação e executar em um ambiente isolado chamado container._

_Este isolamento permite a execução de muitos containers em um determinado host. Inclusive esse host pode ser uma máquina virtual._

---------------------------------------------------------------
## Como esse isolamento funciona ?

*Também conhecido como Docker Internals, o docker utilizar algumas features do kernel linux para prover este isolamento.*

**Irei focar nos principais módulos do kernel que o Docker utiliza:**

* ### Namespaces: 
    _Fornece o isolamento para que outras partes do sistema permaneçam inalteradas pelo que estiver dentro desse namespaces_

        Tipos de namespaces:

            PID namespace
            NET namespace
            IPC namespace
            MNT namespace
            UTS namespace
            User namespace

* ### Cgroups: 
    _Fornece o isolamento de recursos, tais como:_

        CPU
        Memory
        Network Bandwidth
        Disk
        Priority

* ### Netfilter: 
    _Módulo do firewall responsável por criar as regras para o containers, como por exemplo o redirecionamento de portas._
----------------------------------------------------------
## Arquitetura do Docker:

![Arquitetura Docker](https://www.jlcp.com.br/wp-content/uploads/2020/01/docker-arquitetura.png)

**A arquitetura do Docker é composta por:**

    Docker Daemon;
    Docker Client;
    Docker Registry.

**Docker Daemon:**

_Possui um processo chamado dockerd, escuta as requisições da API do Docker e gerencia os objetos:_

    Imagens
    Containers
    Redes
    Volumes

_É possível se conectar com outros daemon para gerenciar serviços Docker._

----------------------------------------------------------

**Docker Client:**

_Utilizado para interagir com o docker, o docker client envia os comandos ao dockerd que os executa. O docker cliente pode se comunicar com mais de um daemon._

----------------------------------------------------------
 
**Docker Registry:**

_O docker registry é responsável por armazenar e distribui as imagens docker. Por padrão o registry utilizado é o Docker Hub. Você executar o seu próprio registry privado ou utilizar em cloud, **por exemplo:**_

    Amazon Elastic Container Registry (ECR)
    Azure Container Registry (ACR)
    Google Container Registry
    Entre outros.

----------------------------------------------------------
 
## O que são imagens?

_Podemos dizer que uma imagem é a aplicação que queremos executar._

_É um modelo somente leitura com instruções para a criação de um container._

_Toda imagem possui como base uma outra imagem e nela aplicamos as customizações necessárias para nossa aplicação._

**Exemplos:**

    Utilizamos como imagem base o Ubuntu
    Instalamos o NGINX
    Copiamos o nosso arquivo de configuração do NGINX para a imagem.
    Copiamos o código fonte da nossa aplicação
    Fazemos o build da imagem e enviamos para o registry.

 ----------------------------------------------------------

## O que são containers Docker ?

_Um container é uma instancia de uma imagem sendo executada de forma isolada no host._

_Podemos dizer que ao iniciar um container, carregamos uma imagem e as opções de configurações disponíveis, **tais como**:_

    Variáveis de ambiente;
    Portas de rede;
    Volumes;
    Entre outros.

_Quando um container é removido suas alterações de estados que não sejam persistidas irão ser removidas._

----------------------------------------------------------
 
## Qual a vantagem em utilizar containers ao comparado a uma máquina virtual?

_Uma das vantagens de utilizar containers é que você não precisa de uma camada hypervisor porque os containers são executados diretamente no kernel da máquina host como um processo._

_Desta forma você reduz o trabalho operacional de provisionar uma máquina seja ela física ou virtual para cada aplicação, sendo assim irá utilizar o mesmo hardware do host para executar múltiplos containers._

**Vamos utilizar o seguinte cenário para fixar este conceito.**

_Na empresa que você trabalha é utilizado um hypervisor para disponibilizar máquinas virtuais para cada aplicação._

_Seu gerente lhe passa uma demanda de fazer o deploy de 5 máquinas virtuais novas para hospedar por exemplo 5 sites._

## **Virtualização:**

_A área de infraestrutura iria seguir o seguinte fluxo:_

* **Criar cinco (5) máquinas virtuais**
* **Instalar o sistema operacional.**
* **Atualizar o sistema operacional e instalar os pacotes básicos.**
* **Instalar pacotes e dependências para aplicação.**
* **Configurar a aplicação.**

![img](container-vm-whatcontainer_2.webp)

-----------------------------------------------------------------

## **Docker:**

* **Criar uma (1) máquina virtual.**
* **Instalar o sistema operacional.**
* **Atualizar o sistema operacional e instalar os pacotes básicos.**
* **Instalar o docker.**
* **Iniciar o container**

![img2](https://www.jlcp.com.br/wp-content/uploads/2020/01/docker-containerized-appliction-blue-border_2.png)

_Cada aplicação irá executar um novo container._

_Neste caso você irá gerenciar somente uma máquina virtual reduzindo o tempo de entrega da infraestrutura e também o trabalho operacional._