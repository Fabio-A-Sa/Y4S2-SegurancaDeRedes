# Project Submission

Smurf Attack

Tipo de ataque DDoS, onde o atacante envia em broadcast para toda a rede um grande número de solicitações echo ICMP com IP de origem falsificado. Deste modo, os workers/pcs da rede respondem a esse IP, que é o IP da vítima (conseguido por sniffing, spoofing), garantindo que esta fica sem recursos para responder às solicitações legítimas.
Fraggle attack é uma variação deste, em vez de ICMP usa-se UDP.

Protótipo:

- Simulação de uma rede;
- Um nó como vítima a rodar uma aplicação, um router, os restantes como workers;
- Admite-se que a rede está comprometida (botnet);
- Tecnologias usadas: Unix systems, scapy (python library), docker (?);

Explorações:

- Exploração teórica da história por detrás deste tipo de ataque;
- Simulação prática do Smurf attack no protótipo desenvolvido;
- Mitigação teórica e prática deste ataque, como 
    1. disabling IP directed broadcasts on routers
    2. configuring network devices to filter or rate-limit ICMP traffic
- Simulação prática do Fraggle attack como variante do Smurf attack;
- Mitigação teórica e prática do Fraggle attack de forma semelhante ao anterior;