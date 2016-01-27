# Data Processing (sahara)
---

O projeto Sahara provê uma maneira simples de gerenciar uma aplicação intensa em tratamento de dados clusterizados (Hadoop ou Spark), em cima da arquitetura OpenStack. O usuário deve informar parâmetros como versão, topologia do cluster, detalhes dos nós do hardware e mais para integrar com os sistemas mencionados, de maneira que o Sahara possa tornar o tratamento desses dados escalável e se ajustando _on demand_ de acordo com a clusterização.

### Detalhes Gerais
O produto sahara se comunica com os seguintes serviços OpenStack:
* Dashboard (Horizon) - fornece uma interface gráfica com capacidade de usar todos os recursos do Saara
* Identity (Keystone) - autentica os usuários e fornece tokens de segurança que são usados ​​para trabalhar com OpenStack, limitando capacidades de um usuário em sahara aos seus privilégios OpenStack
* Compute (nova) - utilizado para fornecer VMs para clusters de processamento de dados
* Orchestration (heat) - utilizado para fornecer e orquestrar a implantação de clusters de processamento de dados
* Imagem (glance) - armazena imagens de VM, cada imagem que contenha um sistema operacional e uma distribuição de processamento de dados pré-instalado ou quadro
* Object Storage (swift) - pode ser utilizado como armazenamento para os binários de emprego e dados que serão processados ​​ou criados por trabalhos de enquadramento
* Block Storage (cinder) - pode ser usado para armazenamento em bloco provisão para instâncias VM
* Networking (neutron) - fornece serviços de rede para clusters de processamento de dados
* Telemetria (ceilometer) - usado para coletar medidas de uso de cluster para fins de medição e monitoramento

---

...

### Arquitetura
A arquitetura Sahara consiste em vários componentes:
* Componente Auth - responsável pela autenticação e autorização do cliente, se comunica com o serviço OpenStack Identity (Keystone)
* DAL - Data Access Layer persistir modelos internos no BD
* Provisioning Engine - componente responsável pela comunicação com o OpenStack Compute (nova), Orchestration (heat), Block Storage (cinder) e serviços de imagem (glance)
* Vendor Plugins - mecanismo responsável pela configuração e lançamento de estruturas de processamento de dados em VMs provisionados. Soluções de gerenciamento existentes, como o Apache Ambari e Console de Gerenciamento de Cloudera poderia ser utilizado para esse fim também
* EDP - Processamento de Dados Elastico (EDP), responsável pela programação e gerenciamento de tarefas de processamento de dados em clusters provisionados por sahara
* API REST - expõe a funcionalidade sahara via interface REST HTTP
* Python Sahara Client - como outros componentes OpenStack, sahara tem seu próprio cliente python
---

...
