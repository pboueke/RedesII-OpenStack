# Database Service (Trove)
---

Trove é um banco de dados como serviço do OpenStack, e portanto foi planejado e pensado para funcionar inteiramente com o OpenStack, com o objetivo de permitir aos usuários utilizar facilmente as funcionalidades de um banco de dados relacional ou não-relacional sem a necessidade de tratar questões administrativas complexas. Usuários e DBAs podem gerenciar múltiplas instâncias de bancos de dados conforme necessário.

## Arquitetura
### trove-api
O serviço trove-api oferece uma API RESTful que suporta JSON e XML para provisionar e gerenciar instâncias Trove
* Um componente RESTful
* Ponto de entrada - Trove/bin/trove-api
* Usa um launcher de WSGI configurado pelo Trove/etc/trove/api-paste.ini
* * Define o pipeline de filtros; tokenauth, Ratelimit, etc.
* * Define o app_factory para o troveapp como trove.common.api:app_factory
* A classe API (roteador WSGI) conecta os caminhos REST para os controladores adequados
* Controladores geralmente redirecionam a execução de uma classe no módulo models.py
* Neste ponto, um módulo de API de outro componente (TaskManager, GuestAgent, etc.) é utilizada para enviar o pedido para a frente através RabbitMQ

### trove-taskmanager
O serviço trove-taskmanager faz o trabalho pesado, tanto quanto o provisionamento casos, gerenciar o ciclo de vida de instâncias, e realizando operações na instância do banco de dados.
* Um serviço que escuta em um tópico RabbitMQ
* Ponto de entrada - Trove/bin/trove-taskmanager
* Funciona como um RPCService configurado pelo Trove/etc/trove/trove-taskmanager.conf.sample que define trove.taskmanager.manager.Manager como o gerente - basicamente este é o ponto de entrada para as solicitações que chegam através da fila
* Tal como descrito acima, para este componente de pedidos são empurrados para MQ a partir de outro componente através do módulo TaskManager API usando _cast () ou _call () (sincronia / a-sync) e colocando o nome do método como um parâmetro
* Trove/OpenStack/ rpc/RpcDispatcher.dispatch common/ dispatcher.py- () chama o método apropriado no Gerenciador por algum equivalente a reflexão
* O gerente, então, redireciona o manuseio de um objeto a partir do módulo models.py. Ele carrega um objeto da classe relevante com o contexto e instance_id
* Manuseamento real geralmente é feito no módulo models.py

---

...
