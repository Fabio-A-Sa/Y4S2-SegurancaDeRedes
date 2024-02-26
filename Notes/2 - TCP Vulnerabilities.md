# TCP Sequence number attacks

O TCP SYN flooding é um tipo de vulnerabilidade em TCP, já abordado anteriormente:

O servidor fica indisponível quando o atacante envia muitos pedidos SYN, pois fica sem memória para guardar o estado de todas as ligações. Aí as ligações TCP legítimas não são atendidas. 

## Vulnerabilidades

### Spoofing TCP Session establishment

Se o atacante souber o número de sequência que é usado para a ligação TCP, poderá interceptar as requests. É mais simples em UDP, mas não impossível em TCP, mesmo que não sabia a resposta do servidor na altura, pois é com base em incrementos. 

### TCP Session Hijacking

Injecta pacotes na conexão TCP, com uma possível perda de sincronização entre os endpoints: ocorre um *deadlock* quando tanto o cliente como o servidor rejeitam os headers dos pacotes, pois os valores não são os expectáveis.



### TCP Reset