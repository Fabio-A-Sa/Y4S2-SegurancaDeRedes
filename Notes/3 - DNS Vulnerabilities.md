# DNS Vulnerabilities

Para transformar nomes em endereços IPs, cujo mapping é guardado em `/ect/hosts` e os servidores que podem ser usados no DNS local no ficheiro `resolv.conf`. Acima desta configuração existe um **DNS Cache** e após isso um **DNS Server**. A procura da resolução pode ser iterativa, não recursiva ou recursiva, e em Linux existe o comando `dig` para procurar o respectivo IP.

Não existe muita segurança neste protocolo, existindo apenas:

- Transactio ID;
- Client UDP port number;

As firewalls normalmente não filtram o tráfico DNS, permitindo **tunneling** (recebe dados através de pacotes DNS) e **exfiltration** (criação de subdomínios para receber informação) como comuns ataques.

## Vulnerabilidades

### Misleading domain names

É uma vulnerabilidade humana, através de simples typos no endereço ou utilização de outros alfabetos. 

### Compromise the victim's host

Mudanças nos ficheiros `/ect/hosts` ou `resolv.conf`, assim como alterações nas suas permissões.

### Spoofing a local DNS cache

Podemos sniffar a rede do cliente, permitindo um spoofing do DNS reply mais rápido do que o legítimo, mandando um IP controlado pelo atacante.

### Poisoning a DNS cache

#### Local

Se se conseguir manipular a request/reply entre o DNS Cache e a Internet (DNS Server), estando o atacante na rede, acabamos por conseguir manipular o conteúdo do DNS Cache (local). O spoofing tem de ser também mais rápido que a resposta legítima.

#### Remote

Quando o atacante está remoto, não consegue adivinhar à partida as requests de dentro da rede (sniffing difícil). No entanto, dá para fazer trigger de um DNS request, e spoofing do DNS transaction ID e UDP client port number. A ideia é negar o efeito da cache, fazendo request de nomes random sobre o mesmo domínio: ABCDEF.up.pt, por exemplo, até que o DNS Cache fique modificado.

### Reply forgery / poisoning from malicious DNS server

Se um DNS server for comprometido, o DNS cache poderá dar append a informação não legítima, mesmo que o IP o seja, através de spoofing de alguns campos.

### DNS rebinding

Quando queremos atacar um servidor não acessível (está dentro de uma rede interna). Ao rodar código malicioso JS na máquina da vítima consegue ativar uma nova resolução de IP, mas como o SOP (*Same Origin Policy*), essa request é possível.

### DoS

- Muitos pedidos para atacar a estabilidade, com spoofing;
- Ataques de amplificação, onde a request é curta mas a resposta pode ser longa, comprometendo memória;
- `NXDOMAIN`: pedidos a DNS servers, quando não existe IP respectivo e portanto os DNS caches não impedem;
- `NXNSAttack`: as requests/replies são delegadas entre resolvers;