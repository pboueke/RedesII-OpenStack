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

## Segurança no OpenStack

### Projeto de Segurança
