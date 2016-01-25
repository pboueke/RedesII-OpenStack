# Dashboard (horizon)
O Horizon providencia uma interface gráfica para os usuários acessarem, provisionarem e automatizarem recursos da nuvem. Horizon começou como um único aplicativo para gerenciar projeto de computação do OpenStack. Como tal, tudo o que precisava era de um conjunto de pontos de vista, modelos e chamadas de API. De lá, ele cresceu para apoiar vários projetos OpenStack e APIs gradualmente, dispostos de forma rígida em "dash" e "agrupamentos syspanel".

Na sua essência, Horizon deve ser um padrão de registro para aplicações se conectarem.

A aplicação Horizon também vem com um conjunto de abstrações de API para os projetos do núcleo OpenStack, a fim de fornecer um conjunto consistente e estável de métodos reutilizáveis para desenvolvedores. Usando essas abstrações, desenvolvedores trabalhando com o Horizon não precisam estar intimamente familiarizados com as APIs de cada projeto OpenStack.

Para instalar o Horizon precisa-se compilar catálogos de mensagens tradução para a internacionalização. Este passo não é necessário se você não precisa de suporte a outros idiomas além do Inglês. A ferramenta GNU gettext é necessária para compilar catálogos de mensagens:

$ sudo apt-get install gettext
$ ./run_tests.sh --compilemessages

Este comando compila catálogos de mensagens tradução dentro Python virtualenv chamado .venv. Após esta etapa, você pode remover o diretório .venv com segurança.

Instale o módulo python Horizon em seu sistema. Execute o seguinte no diretório raiz:
$ sudo pip install .

Crie a pasta openstack_dashboard/local/local_settings.py. É geralmente uma boa idéia para copiar openstack_dashboard / local / local_settings.py.example e editá-lo. Pelo menos temos de personalizar as seguintes variáveis neste arquivo
* ALLOWED_HOSTS (a não ser que DEBUG seja True)
* OPENSTACK_KEYSTONE_URL


Configure um servidor Web com suporte WSGI. É opcional, mas recomendado em implantações de produção. Por exemplo, instalar o servidor web Apache no Ubuntu:
$ sudo apt-get install apache2 libapache2-mod-wsgi
