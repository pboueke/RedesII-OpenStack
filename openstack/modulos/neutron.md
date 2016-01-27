# Networking (neutron)

Neutron é um projeto OpenStack para fornecer NaaS entre dispositivos de interface (i.e. vNICs) gerido por outros serviços OpenStack (i.e. Nova).

A arquitetura exemplo com OpenStack Networking (Neutron) exige um nó controlador, um nó de rede, e pelo menos um nó de computação. O nó controlador contém uma interface de rede na rede de gestão. O nó de rede contém uma interface de rede na rede gestão, uma na rede de túneis de instância e um na rede externa. O nó de cálculo contém uma interface de rede na rede e gestão de uma rede de túneis na instância.

O Neutron providencia uma API para construir topologias de redes ricas, e configurar políticas de rede avançadas em nuvem. Permite construir plugins (fonte de inovação aberta e fechada) que introduzem capacidades avançadas de rede e providencia uma API de extensibilidade Framework, incluindo as extensões para " rede do provedor ", que mapeia redes Neutron L2 a uma VLAN específica no centro de dados físico
