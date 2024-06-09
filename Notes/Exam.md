# Exam questions & answers

## Network Vulnerabilities

- O que é vulnerabilidade? Dá exemplos segundo as cinco categorias.

Fraqueza do sistema que pode ser aproveitada por um atacante para aceder a dados sensíveis e ter controlo. Podem derivar de implementation bugs, flaws em algoritmos e protocolos, acessible attacks points, user related e Denial of Service.

- Diferença entre sniffing and spoofing.

Sniffing fica só a ver o que passa na rede, enquanto que spoofing cria e injecta novos pacotes na rede. Devido a protocolos de segurança Spoofing é mais complexo de implementar.

- O que é IP Route Spoofing?

Utiliza uma terceira máquina para enviar um TCP SYN/ACK, para receber os pacotes em vez da vítima. Utiliza um helper do pacote.

- Smurf Attack? ICMP?

Usado em ICMP (echo/reply), envia um echo em broadcast, e a vítima recebe os replays (porque no pacote em spoofing tem source = victim).

- ARP e ARP Poisoning?

O protocolo ARP traduz IPs em MAC addresses. Man-in-the-middle attack, onde o atacante faz droppar ou até spoofing, anunciando-se como titular do IP.

- VLAN Hooping?

Para atingir uma VLAN isolada, pode usar IP packets com appends no destinatário. Quando passa por um router intermédio, perde a tag inicial (VLAN dele, VLAN da vítima, resto do payload) e o seguinte será o destino: o pacote chega ao destino solicitado, mesmo que o atacante esteja fora da VLAN selecionada.

- TCP SYN Flooding?

Com muitas requests SYN, acaba por gastar a memória do servidor e garantir que ligações legítimas sejam droppadas. É um Denial of Service.

- Tear Down Attack?

Quando IP packets são fragmentados, mas devido a erros do offset acabam por dar overflow e crashar o servidor.

- Ping of Death?

Quando a soma de offsets de ICMP packets ultrapassa o possível, ocorrendo overflow/underflow e crashando também o servidor.

- TLS Hearth Bleed?

Antigamente a resposta do TLS envolvia um payload random de N bits que era pedido na request, sem contar que se N fosse muito grande poderia comer a memória sensível do servidor.

- Land Deniel (LAND)?



- Echo Chargen Attack?

- TCP Session stablishment session spoofing?

- TCP Hijaking?

- TCP Reset attack?

- Como funciona o DNS?

DNS possui transition ID e UDP Ports.

- Enumera ataques possíveis ao DNS.

- Diferenças entre o DNS poisoning a nível local e remote?

- Define o RIP protocol.

- Define o BGP protocol.

- Define o OSPF protocol.

## Active Defense

- Definição de Firewall e VPN e suas diferenças.

- O que faz o EBPF.

- O que são NATs e diferenças em relação às Firewalls?

- Firewalls stateless and statefull.

- Define e indica características de Zero Trust Security.

- Firewall como Proxy: diferenças entre transparente e não transparente.

- Host-to-net VPNS: diferenças entre layer-free e layered VPNS.

- Intrusion Detection Systems: Host and Network, diferenças.

- Intrusion Detection Systems: Knowledge and Behavioral, diferenças.

Um deles é semelhante a VPNs, porque funciona com base em regras definidas.

- Importantes Network data types para IDS.
 
## Authentication Protocols

- Como funcionam os Smart Cards?

Importante dizer que 

- Que benefícios possui o SSO em relação aos logins tradicionais?

- Definir as principais etapas do TLS. Perfect Forward Secrecy, como é que o TLS garante isso?

- 802.11

- IPSec

- DNSSEC, e seus derivados problemas

- Securing BGP

- Definições como Secury Multiparty Computation, Domain name attacks, MISP, OSINT, sandboxing and honeypots.