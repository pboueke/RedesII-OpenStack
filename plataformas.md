# Concorrência e Integração com outras Plataformas

## Integração com Diferentes Hypervisors

### O que é Hypervisor?

Um hypervisor é a peça central da virtualização. Esse componente é o que faz de fato a simulação de um hardware, permitindo rodar, nos mesmos recursos, dois ou mais sistemas operacionais, que não enchergam um ao outro. Basicamente virtualizando todos os recursos e simulando uma máquina física e passando isso para o Sistema Operacional.

Existem dois tipos de Hypervisors:

* **Hypervisor tipo 1**, ou *nativo*: Este é chamado de nativo pois ele roda diretamente sobre o hardware, sem a necessidade de um sistema operacional intermediário. Isso possibilita uma melhor utilização dos recursos e diminui o gasto. Útil para implantações com diversos nós.
* **Hypervisor tipo 2**, ou *hospedado*: Este é chamado hospedado pois é um software que roda sobre um dado sistema operacional, portanto alocações de memória, chamadas de disco normalmente tem de passar pelo sitema operacional e pelo sistema de arquivos. Alguns permitem que você crie uma partição com um sistema de arquivos especial para agilizar a escrita em disco. A vantagem é que a instalação é mais fácil e permite que você rode ele juntamente com outros programas.

### Hypervisors Suportados

Quando se trata de nós de computação eles por default já vem, junto com o agente do Nova, com um hypervisor padrão do OpenStack. Entretanto é possível integrar diferentes Hypervisors, tanto tipo 1 quanto tipo 2.

Dentre os Hypervisors suportados estão:
* VMware
* KVM
* XenServer
* Xen Cloud Platform (XCP)
* Hyper-V

Vale lembrar que ao utilziar um Hypervisor tipo 1, o que rodará juntamente ao nó de computação e ao agente do Nova será apenas o agente do hypervisor, porque para realmente rodar as máquinas virtuais são necessárias outras máquinas dedicadas.

## Alternativas

### Apache CloudStack

O Apache CloudStack é a concorrência mais direta com o OpenStack. Implementa todas as coisas básicas do OpenStack, inclusive de formas similares e além disso implementa algumas das funcionalidades extras.

### HP Helion Eucalyptus

O HP Helion Eucalyptus é uma implementação da núvem da AWS, baseada no OpenStack focada em possibilitar que aplicações AWS rodem nas máquinas on-premise.

O HP Helion é um conjunto de programas open-source que são mantidos pela HP, baseados em OpenStack e incluem, inclusive, uma distribuição do OpenStack customizada.

### Google's Ganeti

O Google Ganeti é o mais diferente entre os citados anteriormente. Ele adota uma forma mais minimalista, permitindo começar funcionalidades de um IaaS de forma incremental, partindo de pequenos componentes. Segue uma filosofia familiar a usuários de sistemas baseados em UNIX, que são pequenos componentes que fazem poucas coisas e que se complementam muito bem.

É o que tem a maior facilidade para começar, mas também é o que menos dita as formas de se fazer as coisas, o que abre mais espaço para que pessoas inexperientes cometam erros ao implantar uma núvem utilizando o Ganeti.
