# DNS Vulnerabilities

Para transformar nomes em endereços IPs, cujo mapping é guardado em `/ect/hosts` e os servidores que podem ser usados no DNS local no ficheiro `resolv.conf`. Acima desta configuração existe um **DNS Cache** e após isso um **DNS Server**. A procura pode ser iterativa, não recursiva ou recursiva, e em Linux existe o comando `dig` para procurar o respectivo IP.

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

Quando o atacante está remoto, não consegue adivinhar à partida as requests de dentro da rede (sniffing difícil). No entanto, dá para fazer trigger de um DNS request, e spoofing do DNS transaction ID e UDP client port number. A ideia é negar o efeito da cache, fazendo request de nomes random sobre o mesmo domínio: ABDCSA.up.pt, por exemplo, até que o DNS Cache fique modificado.

### Reply forgery / poisoning from malicious DNS server



### DNS rebinding



### DoS

