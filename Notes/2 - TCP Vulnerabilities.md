# TCP Sequence number attacks

O TCP SYN flooding é um tipo de vulnerabilidade em TCP, já abordado anteriormente:

O servidor fica indisponível quando o atacante envia muitos pedidos SYN, pois fica sem memória para guardar o estado de todas as ligações. Aí as ligações TCP legítimas não são atendidas. 

## Vulnerabilidades

### Spoofing TCP Session establishment

Se o atacante souber o número de sequência que é usado para a ligação TCP, poderá interceptar as requests. É mais simples em UDP, mas não impossível em TCP, mesmo que não sabia a resposta do servidor na altura, pois é com base em incrementos. 

### TCP Session Hijacking

Injecta pacotes na conexão TCP, com uma possível perda de sincronização entre os endpoints: ocorre um *deadlock* quando tanto o cliente como o servidor rejeitam os headers dos pacotes, pois os valores não são os expectáveis.

A ligação TCP:

- Suporta numeração de pacotes mesmo sem ordem;
- A aceitação de pacotes fora de ordem depende também do tamanho do receiver buffer;
- O atacante pode enviar um range de bytes que implique um possível *deadlock*;

### TCP Reset

A forma correcta de terminar a conexão TCP, que pode ser despoletada tanto do lado do servidor como do cliente, é enviar pacotes do protocolo `FIN/ACK` com os correspondentes números de sequência.

No entanto, uma das partes pode enviar também um pacote RST (*reset*), enviando também um número de sequência. Se houver `sniffing`, é possível descobrir o número pretendido e obrigar ao reset da ligação para comprometê-la.