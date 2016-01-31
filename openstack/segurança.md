# Segurança

Quando se fala sobre qualquer coisa que envolva redes de computadores, segurança é de fato uma preocupação iminente. Ao se tratar de Computação em Núvem, as medidas devem ser tomadas tanto pelo provedor da infraestrutura quanto pelos usuários da rede, portanto devemos relembrar do que foi apresentado em [Modelos de Implantação](../introducao/nuvem/implantacao.md).

## Requisitos do Provedor

O provedor de uma infraestrutura em núvem deve garantir:

* **Autenticação**: Discernir cada um dos seus usuários.
* **Autorização**: Garantir que cada usuário tenha acesso apenas aos recursos que lhe são de direito.
* **Disponibilidade**: Os recursos alocados por cada usuário devem ser garantidos integralmente.
* **Privacidade**: Garantir que todas as informações criticas de seus usuários sejam guardados de forma encriptografada e que nenhuma infromação saia dos limites estipulados.

Para atingir esse objetivo, o provedor deve além de verificar que o software gestor da núvem (como o OpenStack, por exemplo) provê ferramentas para tais pontos deve também garantir o que se chama de **Segurança Física**, isto é, garantir que os computadores, discos e qualquer dispositívo fisico esteja seguro de acessos não autorizados, incêndios, alagamentos.

Além disso existe também a **Segurança de Pessoal**, que envolve em garantir através de termos e contratos que as pessoas envolvidas com o provedor e os clientes todos estejam de acordo com normas e clausulas de sigilo, privacidade e termos de uso.

## Segurança de Aplicação

O provedor deve fornecer algumas garantias básicas e pode obrigar as aplicações a seguirem algumas obrigações de segurança, entretanto, muitas das preocupações o provedor pode apenas dar oreintações ou apenas indicar que algum problema pode emergir. Portanto, as garantias finais de segurança ficam no nível da aplicação (SaaS), deixando para os usuários do provedor o trabalho de suprir tais requisitos.

## Preocupações

Uma das maiores preocupações com Cloud Computing está relacionado aos dados utilizados pela aplicação, muitas das vezes dado a perda de controle físico das coisas pelos usuários.

Já que o armazenamento nas máquinas virtuais é volátil, muitas das vezes é necessário guardar informações em outro sistema, fora da aplicação e isto levanta muitas possíveis opções para vazamento de informações privativas.

Além disso o usuário não se preocupa mais com a forma física de armazenamento, deixando toda a responsabilidade de tolerância a falhas com o provedor.

## Segurança no OpenStack

### Projeto de Segurança

O _Security Project_ é um grupo dedicado a fornecer os requisitos de segurança que envolve membros de diversos times do OpenStack.
Os pilares do projeto são:

* **Orientação de Desenvolvedores**: Ajudar os desenvolvedores a tomar medidas para prover segurança em cada um dos módulos e plugins do OpenStack
* **Notas de Segurança**: Postagens de informações sobre possíveis preocupações a serem tomadas. Pode ser verificado no link [Security Notes](https://wiki.openstack.org/wiki/Security_Notes)
* **Guia de Segurança**: Um guia escrito contendo todas as informações relevantes para segurar uma implantaçao do OpenStack
* **Análise de Ameaça**: Analisar ameaças e quando encontradas lançar avisos sobre. [Security Advisories](https://security.openstack.org/ossalist.html)
* **Auditoria de Criptografia**: Realizar auditoria dos métodos criptográficos em todos os módulos do OpenStack.
* **Teste de APIs**: Testar apis supostamente seguras para buscar falhas.
* **Desenvolvimento de Módulos**: Além disso alguns módulos são desenvolvidos para auxiliar as tarefas:
* * **Bandit**: Analisador de Árvore de Sintaxe Abstrata(AST) de programas python para buscar falhas de segurança.
* * **Anchor**: Uma infraestrutura de Chaves Públicas para servir como centro de confiança entre os serviços do OpenStack.
