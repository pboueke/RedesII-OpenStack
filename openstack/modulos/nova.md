# Compute (nova)

Nova é um projeto OpenStack projetado para fornecer recursos de computação massivamente escaláveis sob demanda.
Ela foi construído sobre uma arquitetura nada compartilhada baseada em mensagens. Todos os principais componentes do Nova podem ser executados em vários servidores. Isto significa que a maior parte da comunicação componente a componente deve ser feita via fila de mensagens. A fim de evitar o bloqueio cada componente enquanto espera por uma resposta, usamos objetos diferidos, com um callback que é acionado quando for recebida uma resposta.

Os principais componentes do Nova são:
* BD (normalmente é uma instância compartilhada com outros componentes do OpenStack): banco de dados SQL para armazenamento de dados. Usado por todos os componentes
* Painel Web: potencial componente externo que se comunica com a api
* API: componente que recebe solicitações HTTP , converte comandos e se comunica com outros componentes através da fila ou http
* Auth Manager: componente responsável por usuários, projetos e papéis ("roles")
* Objectstore: servidor http que replica a api s3 e permite o armazenamento e recuperação de imagens
* Scheduler: decide qual host recebe cada VM
* Rede: gerencia IP Forwarding, pontes e vlans
* Compute: gerencia a comunicação com máquinas virtuais e hypervisor
