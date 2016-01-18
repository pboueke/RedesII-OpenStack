# Virtualização
---

Se trata da execução de um sistema operacional ou aplicação em uma plataforma de hardware simulado que permite o compartilhamento do hardware físico entre múltiplos processos. Essa abordagem flexibiliza o processo produtivo por agilizar a alocação de recursos e diminuir os custos de manutençao, aumentando a escalabilidade do sistema.

O hardware virtualizado é gerenciado por um software ou firmware chamado de *hypervisor*, ou *VMM* (*Virtual Machine Manager*) em uma máquina *host*. Os principais métodos de virtualização de hardware consistem de:

* **Virtuzalização Completa**: simulação quase completa do hardware para permitir a execução de softwares não modificados.
* **Virtualização Parcial**: nem todos os componentes são simulados,o que pode gerar complicações na execução de softwares não modificados.
* **Paravirtualização**: softwares executados precisam estar adaptados especificamente a esse tipo de ambiente, no qual o hardware não está sendo simulado, mas cada máquina *guest* está segregada em um domínio próprio.

Os principais pontos nos quais a virtualização se destaca são:

* Reduzir os custos;
* Alta disponibilidade;
* Redução da ociosidade;
* Eficiência;
* Alocação de recursos;
* Manutenibilidade;
* Gerenciamento.
