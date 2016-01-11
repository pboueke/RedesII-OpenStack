# Identity (keystone)
O Keystone é um front-end HTTP para vários serviços. Como outras aplicações OpenStack, isso é feito usando interfaces python WSGI e os aplicativos são configurados em conjunto, utilizando o Paste. Pontos de extremidade HTTP do aplicativo são compostos de pipelines de WSGI middleware. Sua arquitetura divide funcionalidades em: Identity, Resource, Assignment Token, Catalog e Policy.

O serviço de Identity providencia validação de credenciais e informações para usuários e grupos;

Ao passo que o Resource provê dados sobre Projetos e Domínios. Como o serviço de Identity, estes dados podem ser gerenciados diretamente pelo serviço ou serem puxados de outro serviço de backend, como o LDAP;

O serviço de Assignment fornece dados sobre Roles atribuições de Role às entidades geridas pelos serviços de Identity e de Resource. Novamente, como esses dois serviços, este dados podem ser gerenciadas diretamente pelo serviço de Assignment ou serem puxados de outro serviço de backend, como o LDAP;

O serviço de Token valida e administra tokens utilizados para autenticar solicitações de uma vez as credenciais do utilizador tenham sido verificados;

O serviço Catalog fornece um registro de terminal utilizado para a descoberta de endpoint;

O serviço Policy fornece um mecanismo de autorização baseado em regras e a interface de gerenciamento das regras associadas;
