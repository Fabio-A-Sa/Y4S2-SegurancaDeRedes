# Routing Vulnerabilities

As routing tables, adaptadas por routing messages, são essenciais para garantir um protocolo de encaminhamento fiável. Para cada IP existe uma porta preferencial associada.

Principais consequências de ataques a nível de routing:

- ver os pacotes trocados (*eavesdropping*);
- congestionar, criar instabilidade;
- particionar a rede;
- *blackholing*, fazer com que os pacotes sejam descartados;

## Vulnerabilidades

### Routing attack 

Injectando routing messages que trocassem o flow da rede, permitindo que os pacotes passassem também pela máquina do atacante.

### RIP (Routing Information Protocol) attacks

É um protocolo regido por distâncias, onde cada router indica as distâncias dos seus vizinhos e ao nó de destino pretendido. Como possuia muito pouca segurança, os ataques consistiam em:

- um host assumir-se como router;
- um router indicar distância zero ao destino, fazendo com que os pacotes passassem por ele;
- um router indicar distância maior ao destino, afastando os pacotes;
- enviar routing messages arbitrárias;

### OSPF (Open Shortest Path First) attacks

É um protocolo baseado em link state, com tabelas de encaminhamento. Cada router anuncia através de LSA messages os seus vizinhos, convergindo para um grafo com caminhos mínimos. Já possui mais segurança que o protocolo RIP, mas fica vulnerável porque:

- Enviar LSA messages falsas, contendo o router do atacante por exemplo;
- Enviar LSA messages de router que não existe;

Enviar LSA messages contendo routers legítimos não funciona, porque mais cedo ou mais tarde esse router vai receber essa mensagem e cancelá-la, através de uma mensagem semelhante. Mensagens com IDs superior prevalecem, no entanto enquanto a situação não é resolvida a rede fica instável.

### BGP (Border Gateway Protocol) attacks

É um protocolo de caminho vetorial, mas além da distância anuncia também os respectivos IDs dos nós. É dado um update com novos caminhos entre subnets sempre que possível. Também não possui muita segurança. Ataques possíveis passam sempre por `falsos updates`, como anúncio de rotas que não existem (não podendo entregar os pacotes ao destino), ou anúncio de subnet prefix que não possui (distância zero ao prefixo) para que os pacotes passem pelo router afetado.