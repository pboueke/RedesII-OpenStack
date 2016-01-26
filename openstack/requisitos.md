# Requisitos

É possível colocar uma implantação inteira do OpenStack em apenas uma máquina. Entretanto a implantação mais minimalista é normalmente dividida em dois ou três nós, sendo a primeira consistida de:

* **1 Nó de Controle**, contendo os módulos:
* * *Keystone*: para autenticação
* * *Glance*: para armazenamento de imagens
* * *Cinder*: para oferecer armazenamento persistente
* * *Neutron*: para prover uma rede virtual
* * *Corretor de mensagens*: como o RabbitMQ, utilizado por diversos módulos
* * *Banco de Dados*: como o PostgreSQL, também utilizado por diversos módulos
* **1 Nó de Computação**, contendo:
* * *Nova Compute* para gestão das máquinas virtuais, muitas vezes conectado a um hypervisor.
* * *Agente do Neutron* para gestão das configurações de rede.

Ao crescer a núvem, um dos primeiros passos é separar o *Neutron* em um nó dedicado, o **Nó de Rede** que inclui também normalmente uma instalação do *Open vSwitch*. Além disso o serviço **Cinder** normalmente acaba indo para nós dedicados de armazenamento. Os nós de computação podem ser escalados horizontalmente, com restrições apenas da rede, mas com crescimento linear do poder de processamento.

Um exemplo de implantaçao minimalista pode ser conferido na imagem abaixo:

![Requisitos mínimos de Hardware. fonte: ](installguidearch-neutron-hw.png)
