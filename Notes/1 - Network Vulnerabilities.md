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