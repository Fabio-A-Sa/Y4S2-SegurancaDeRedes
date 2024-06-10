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

TCP/UPD não estavam preparados para ter source/destination iguais, logo entravam em loop no sistema, gastando recursos.

- Echo Chargen Attack?

Echo requests enviam em payload a request, e ao poder haver spoofing do IP da vítima pode entrar em loop infinito.

- TCP Session stablishment session spoofing?

Se souber o sequence number, pois a sessão é estabelecida com base em incrementos.

- TCP Hijaking?

Spoofing de pacotes de modo a comprometer a sincronização das ligações TCP, a nível de sequence numbers e offsets, mesmo que TCP permita entrega de pacotes fora de ordem. Pode ficar em death-lock.

- TCP Reset attack?

Mandar requests RST para cortar ligações TCP.

- Como funciona o DNS?

DNS possui transition ID e UDP Ports. Há três camadas: host, DNS Cache, DNS provider (external).

- Enumera ataques possíveis ao DNS.

Como nome mal escrito, modificar etc/hosts, spoofing do local cache para o host ficar com dados trocados (replay mais rápido que o legítimo), 

- Diferenças entre o DNS poisoning a nível local e remote?

Em modo remoto é mais complicado pois tem de fazer sniffing primeiro e adivinhar a Transaction ID and UDP Port. Além disso, se não acertar tem de esperar para que aquele dado fique inválido em cache, para um novo get a nível remoto. Para invalidar a cache é só pesquisar por <RANDOM_STRING>.up.pt, de modo a associar uma nova pesquisa externa.

- DNS Rebinding?

Quando um servidor não está acessível, e temos o SOP a garantir que nada externo é corrido dentro da máquina. Mas como SOP só olha para os domínios, são só vistos através do IP, logo acaba por conseguir forjar isso.

- Tunneling & Exfiltration

As Firewalls não costumam filtrar pedidos DNS e Exfiltration é o ato de mandar dados ao up.pt através de <RANDOM_STRING>.up.pt, pois estão no mesmo domínio.

- Define o RIP protocol.

Distance vector protocol. Anuncia a distância aos vizinhos. Ataques: mentir, distância negativa, loops.

- Define o BGP protocol.

Path vector protocol. Anuncia a distância e IDs aos vizinhos. Ataques com falsos updates.

- Define o OSPF protocol.

Link State protocol. Anuncia os seus routers vizinhos. Ataques são so mesmos, mas existem mecanismos de fallback que impedem que haja algo mais do que uma instabilidade.

## Active Defense

- Definição de Firewall e VPN e suas diferenças.

Filtram e controlam pacotes de acesso à rede, verificando portas e IP adresses. São implementadas com recurso a IPTables, que fazer fowarding dos pacotes. As firewalls são deployed com base em internas, externas, screenned networks e screening router.

- O que faz o EBPF.

Permite que o código/pacote seja executado em sandboxing pelo próprio kernel.

- O que são NATs e diferenças em relação às Firewalls?

NAT permite que vários endereços IP privados partilhem o mesmo IP público, por motivos de segurança e eficiência. Roteia os pacotes para o sítio certo. Modifica portanto os endereços IP dos pacotes da rede.

- Firewalls stateless and statefull.

Uma verifica sempre (adequada para IP), outra verifica com os dados com base no que já viu anteriormente (adequado a TCP, para não andar a interromper sempre a ligação).

- Define e indica características de Zero Trust Security.

Não confiar em nada, nem dentro nem fora da organização, verificando sempre tudo. Strong identification, validation, intelligente access control, dynamic adaptation.

- Firewall como Proxy: diferenças entre transparente e não-transparente.

Transparentes são TCP wrapper, não-transparentes usam SOCKS, negociam conexões com SOCKS server para authentication, têm configuração explícita e são mais complexas de utilizar/manipular.

- Host-to-net VPNS: diferenças entre layer-free e layered VPNs.

Layer-free ou Tunnel with IP Routing, funciona como uma IP gateway, que faz forward de pacotes e ações apenas. Com layer (bridge channel) funciona como uma VPN que faz forward de ethernet frames between remote host and the corporate network.

- Intrusion Detection Systems: Host and Network, diferenças.

No host, olhando para os dados e aplicações no sistema. Network olhando para os pacotes que estão na rede.

- Intrusion Detection Systems: Knowledge and Behavioral, diferenças.

Knowledge transforma o conhecimento em regras, behavioral retira conhecimento a partir dos dados (mais adequada para anormal detection, usando os modelos, learning from data). Um deles é semelhante a VPNs, porque funciona com base em regras definidas.

- Importantes Network data types para IDS.

Packet traces, counters and flow data.
 
## Authentication Protocols

- Como funcionam os Smart Cards?

Importante dizer que as chaves não saem dos cartões, existindo todo um processamento/check dentro do microprocessador do cartão, sem passar nada a não ser um booleano para fora. Assim garante segurança. Adequado para quando não se conhece o computador onde se está a fazer a ação.

- Que benefícios possui o SSO em relação aos logins tradicionais?

Acesso aos mais variados serviços sem fazer um login individual ou um registo a cada serviço. Usado dentro de corporações.

- Definir as principais etapas do TLS. Perfect Forward Secrecy, como é que o TLS garante isso?

Handshake, Protocol Negotiation. Há PFS porque a descoberta de chaves não constitui ameaça às sessões anteriores. Master key, key pairs and session keys.

- 802.11

Tem três fases: discovery, authentication and key management. Há garantias de integridade, confidencialidade em todas as chamadas efetuadas na rede.

- IPSec

Como o IP é connectionless e unreliable, dropar pacotes não serve porque não requer ordem. 

- DNSSEC, e seus derivados problemas

É mais provável que venha a receber ataques DoS, para garantir transações seguras a nível do URL. Performance reduzida por conta das verificações, as zonas hierarquicas se forem grandes pode também reduzir a performance e converter-se em belos alvos de DoS.

- Securing BGP

É um path vector protocol, há segurança se se criar conections TCP between routers e verificação de todo o caminho percorrido (full path verification).

- Definições como Secury Multiparty Computation, Domain name attacks, MISP, OSINT, sandboxing and honeypots.