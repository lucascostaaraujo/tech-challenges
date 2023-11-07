a) O que é uma sub-rede e por que é usada em uma VPC?

    - Sub-redes são recursos regionais com intervalos de endereços IP's associados a elas, e as mesmas se encontram disponíveis dentro de uma determinada VPC, que por sua vez é uma rede virtual dedicada a uma conta em um cloud provider, e ela é isolada de maneira lógica de outras redes virtuais na Nuvem.


b) Descreva o conceito de balanceamento de carga e porque ele é importante em uma arquitetura de nuvem.

    - Balanceamento de carga ou load balance é uma técnica utilizada para manter a estabilidade de um servidor quando o tráfego ou o volume de dados é muito grande, sendo muito utilizado muitas vezes como borda. na AWS por exemplo, o mesmo pode funcionar recebendo um cabeçalho de um route 53, e encaminhar para um target group, onde estará lincado a uma instância ec2 que por sua vez, quando liberado a porta no security group, fará uma espécie de "nat", encaminhando porta para a porta onde uma determinada aplicação requisitada estará rodando no container.


c) Como um servidor proxy funciona para intermediar as solicitações entre os clientes e os servidores de destino?

    - O Proxy serve como um intermediador de uma comunicação, onde por exemplo, ao invés de ter uma conexão do cliente setando diretamente um endereço IP de um servidor, o mesmo estará setando o endereço do proxy, que por sua vez encaminhará a comunicação para o servidor.
    - Temos também o proxy reverso, que filtra dados entrantes encaminhando para um determinado destido, conforme é configurado, uma das melhores e mais flexíveis ferramentas que é muito utilizada para os dois propósitos citados anteriormente trata-se do NGINX.

d) O que é NAT e qual é o seu propósito em uma rede?

    - NAT nada mais é do que uma “conversão” de ip publico para ip privado, assim podendo ter acesso a outros servidores fora da rede interna.


e) Explique nas suas palavras, o que acontece quando você acessa um site no seu browser por baixo dos panos?

    - Tudo na internet trata-se de endereçamento IP, então quando acesso um determinado site, o mesmo se traduz em um ou mais endereços ip's atravéz de servidores DNS e uma determminada infraestrutura, onde se programam camadas de segurança e boas práticas para proteger o ambiente interno contra ataques, assim aderindo-se a diversas técnicas como medidas de prevenção se vermos pelo lado da segurança, mas não se resume somente a isso, também temos recursos utilizados no meio do caminho para encurtar a comunicação entre cliente/servidor, trata-se dos CDN's, que servem como um cache economizando tempo de resposta, pois os mesmos são configurados estratégicamente mais próximos de regiões dos clientes.
    - Exemplo completo de conexão:
        - o cliente acessa o site: www.orkut.com
        - A requisição bate no DNS do orkut, e pelo mesmo é encaminhada para um load balance, que por sua vez encaminha a requisição para uma instância EC2 da amazon atravéz de um target group, que encaminha a requisição atravez da porta liberada no security group, e então chegando na instancia, ocorre um encaminhamento de portas para dentro de um container onde roda um frontend em uma determinada porta, e então a tela da aplicação será retornada ao cliente, que conforme for utilizando as funcionalidades, o frontend entrará em comunicação com uma ou mais api "dependendo de sua arquitetura definida" onde as requisições serão processadas e retornadas as respostas para o cliente.
        - OBS: a comunicação do frontend com o backend/api's pode se dar de várias formas, conforme for definida a melhor abordagem para o negócio, EX: pode haver conexão do front diretamente a um ip:porta do backend, pode ser através de um api-gateway "ex: kong", pode se dar também através de uma rota "DNS/loadBalance/TargetGroup/SecurityGroup/InstanciaEC2/Container" etc...