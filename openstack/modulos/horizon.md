# Dashboard (horizon)
O Horizon providencia uma interface gráfica para os usuários acessarem, provisionarem e automatizarem recursos da nuvem. Horizon começou como um único aplicativo para gerenciar projeto de computação do OpenStack. Como tal, tudo o que precisava era de um conjunto de pontos de vista, modelos e chamadas de API. De lá, ele cresceu para apoiar vários projetos OpenStack e APIs gradualmente, dispostos de forma rígida em "dash" e "agrupamentos syspanel".

Na sua essência, Horizon deve ser um padrão de registro para aplicações se conectarem.

A aplicação Horizon também vem com um conjunto de abstrações de API para os projetos do núcleo OpenStack, a fim de fornecer um conjunto consistente e estável de métodos reutilizáveis para desenvolvedores. Usando essas abstrações, desenvolvedores trabalhando com o Horizon não precisam estar intimamente familiarizados com as APIs de cada projeto OpenStack.
