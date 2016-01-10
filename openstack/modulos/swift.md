# Object Storage (Swift)

Swift é um projeto de armazenamento distribuído de objetos em nuvem. com alta disponibilidade e armazenamento consistente de objetos. Foi feito para ser facilmente escalável e com alta disponibilidade, de forma que se consiga guardar e recuperar enormes quantidades de dados rapidamente e com uma *API* simples. É ideal para guardar dados desestruturados, podendo crescer vertiginosamente sem problemas.

O sistema de armazenamento organiza os dados em uma hierarquia:
+ Conta: Representa o mais alto nível de hierarquia

+ Contêiner: Define um *namespace* para objetos. Uma conta pode ter infinitos contêineres.

+ Objeto: Armazena dados num geral, junto com seus metadados se necessário.

![Arquitetura Swift](images/swift_01_arquitetura.jpg "Arquitetura Swift")

## Arquitetura Swift
É composta primordialmente por um servidor proxy, um *ring*, servidores de objeto, servidores de contêiner, servidores de contas e um replicador.


#### Servidor Proxy
O servidor proxy é responsável por conectar o resto da arquitetura Swift. Para cada requisição ele procurará a localização

#### *The Ring*
O *ring* é um mapeamento entre o nome de entidades armazenadas em disco e sua localização física. O mapeamento utiliza zonas, dispositivos, partições e réplicas. O *ring* também é responsável por determinar quais dispositivos serão ativados e replicados em caso de alguma falha.

#### Servidor de Objetos
É um simples armazém de objetos que os guarda em dispositivos locais. Objetos e seus metadados são guardados como arquivos binários. Arquivos deletados são guardados como um arquivo de 0 bytes com extensão .ts (*.tombstone*) para garantir a replicação correta da deleção e impedindo que o objeto reaparecesse por uma falha na rede.

#### Servidor de Contêiner
É responsável por listar os objetos que existem dentro dos contêineres. Ele não sabe aonde o objeto se localiza físicamente, somente que ele pertence a certo contêiner.

#### Servidor de Contas
É responsável por listar os contêineres que pertencem a uma certa conta.

#### Replicador
O replicador é responsável por manter o sistema em um estado consistente em caso de um erro ou falha. O processo de replicação compara dados locais com suas cópias remotas para ter certeza que todas contém a última versão ou foram apagados corretamente. 
