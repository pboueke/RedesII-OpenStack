# Database Service (Trove)
---

Trove e um banco de dados como servico do OpenStack, e portanto foi planejado e pensado para funcionar inteiramente com o OpenStack, com o objetivo de permitir aos usuarios utilizar facilmente as funcionalidades de um banco de dados relacional ou nao-relacional sem a necessidade de tratar questoes administrativas complexas. Usuarios e DBAs podem gerenciar multiplas instancias de bancos de dados conforme necessario.

## Arquitetura
---

Todos os componentes do Trove se comunicam atraves de um barramento de trocas de mensagens, que pode ser executado em diferentes servidores. As mensagens sao mandadas por HTTP, e entao traduzidas e reencaminhadas pelo baraamento, tudo isso de maneira assincrona. Sao cinco os principais componentes do Trove, detalhados em seguida:

1. Servidor API
2. Barramento de mensagens
3. Gerenciador de Tarefas
4. Agente visitante
5. Condutor

### Servidor API

A API e quem torna possivel o controle e comando dos visitantes e arquivamento de dados. As extremidades da API sao servicos web HTTP basicos, que gerenciam autenticacao, autorizacao e comandos basicos e funcionais relacionados ao armazenamento de dados.

O servidor atualmente se comunica com dois sistemas, o Gerenciador de Tarefas e com o agente visitante. Sua comunicacao com o gerenciador de tarefas possui por finalidade gerenciar tarefas complexas e assincronas. Ja sua comunicacao com o usuario visitante ocorre para o processamento de queries e comandos simples, tarefas sincronas.

### Barramento de mensagens

Trata-se de uma fila de mensagens que torna possivel a comunicacao entre as extremidades da API, o gerenciador de tarefas e o usuario visitante. Um evento de transmissao de mensagem tipico comeca com o servidor da API recebendo alguma requisicao de algum usuario. Uma vez autenticado o usuario, a requisicao e avaliada e encaminhada para a fila de processamento, onde modulos de execucao aguardam instrucoes para buscar informacoes nos bancos de dados, e devolver a informacao a API para que ela faca o display correto da informacao.

### Gerenciador de Tarefas

O servico de gerenciador de tarefas faz todo o trabalho pesado de prover instancias e gerenciar os ciclos de vida delas, alem de realizar operacoes nelas. Recebe mensagens do servidor da API, respondendo de acordo com a mensagem de consenso sobre a requisicao, e realiza as tarefas necessarias para realizar o processamento daquela requisicao.

### Agente visitante

O agente visitante e um servico executado dentro da instancia visitante, responsavel por gerenciar e operar o proprio banco de dados. E responsavel por colocar databases online, o que muitas vezes e uma tarefa complicada de se realizar. No futuro, a integracao entre o Heat e Trove diminuirao a carga sobre esse servico.

Cada implementacao de banco de dados possui uma implementacao propria de agente visitante, que deve realizar operacoes naquele banco de dados. Embora eles sejam diferentes entre bases de dados distintas, suas funcoes basicas sao sempre as mesmas.

### Condutor

O condutor e um servico executado no host, responsavel por receber mensagens de instancias de visitantes e atualizar as informacoes no host. Por exemplo, status da instancia atual e status do backup. Assim, essas instancias nao precisam se comunicar diretamente com a base de dados para obter informacoes.
