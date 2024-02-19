# Network Vulnerabilities

Uma **vulnerabilidade** é uma fraqueza que permite ao atacante ganhar acesso ou controlar um sistema. Um conjunto de vulnerabilidades é conhecida como uma **superfície de ataque**. Há vários tipos:

- Falhas em algoritmos e protocolos;
- Implementation bugs;
- Accessible attack points;
- User-related;
- Denial of Service;

Estas vulnerabilidades são documentadas em:

- `CWE`: Common Weakness Enumeration;
- `CVE`: Common Vulnerabilities and Exposures;
- `CPE`: Common Platform Enumeration;

Há dois conceitos essenciais nos ataques:

- `Sniffing`: receber ethernet frames da rede;
- `Spoofing`: criação de frames IP, UDP, ..., e enviá-los ou injectá-los pela rede;

## Network vulnerabilities examples

### IP Route Spoofing

Envia pedidos SYNC/ACK do TCP em nome de uma terceira máquina, spoofing do IP, e através da manipulação do routing helper (header que indica os caminhos intermédios antes de ir para o destino), acaba por interceptar a resposta.

### Smurf

Ataque amplificado onde a ideia é sobrecarregar a rede da vítima. Envia uma ICMP request com o source alterado para o IP da vítima, e isto cria um broadcast de todos as máquinas da rede para a vítima, sobrecarregando-o.

### ARP Spoofing

ARP (Address Resolution Protocol) é um protocolo para, dado um IP, descobrir endereço MAC respectivo. Como a primeira resposta é que conta, o atacante poderá indicar o seu MAC, de modo a interceptar/receber os pacotes. Consegue fazer *eavesdrop*, visualização dos pacotes, ou até um *man-in-the-middle*.

### VLANs hopping

Os pacotes têm um cabeçalho que identifica a VLAN de destino. Com uma VLAN isolation (máquinas distintas em VLANs distintas), se uma das VLANs for a default, pode acabar por eliminar o cabeçalho, permitindo o transporte do pacote pelo meio.

### TCP SYN Flooding

O servidor fica indisponível quando o atacante envia muitos pedidos SYN, pois fica sem memória para guardar o estado de todas as ligações. Aí as ligações TCP legítimas não são atendidas. 

### Tear Drop Attack

Os packets de IPs podem ser fragmentados em menores, existindo sobreposição de alguns, com offsets para a reconstrução do mesmo no destino. O sistema operativo crashava quando era enviado offset fosse maior que o permitido pela memória.

### Ping of Death

A fragmentação do pacote IP é de tal ordem que a soma dos seus fragmentos era superior ao que a memória do lado da vítima suportava, criando um crash.

### TLS Heartbleed

EM TLS existem sessões, com possibilidade de existência de heartbeats para mantê-las. Cada pedido ao servidor enviava um conjunto de dados aleatórios juntamente com o seu size N. O servidor responde também com N. No entanto nunca verificava se existia memória suficiente, pelo que existia possibilidade do servidor enviar partes da sua memória, com passwords, dados confidenciais, entre outros.

### EternalBlue

