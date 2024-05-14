# Security

Pode ser conseguida através destes protocolos:

- 802.11i;
- IPSec;
- DNS;
- BGP;

## 802.11i

Usa atualmente o WPA3, que garante uma proteção maior com AES-256 in Galois counter mode, com SHA-384. Fases da operação:

- `Discovery`: com protocolos de integridade e confidencialidade, usando uma pre-shared key;
- `Authentication`: usando uma master session key para as comunicações posteriores;
- `Key Management`: para não comprometer dados sensíveis, nem mensagens;

No entanto existem algumas vulnerabilidades do WPA2, como por exemplo **key-reinstalation** e **offline dictionaries**. Usa-se, por isso, o protocolo novo: `IKEv2`, com sequence numbers para evitar *replay attacks*.

## BGP

Assegurar o transporte de mensagens pela rede, através de routers adjacentes. Usa-se um endereço especial, grandes caminhos e pequenos prefixos. Além disso, necessita-se de uma autorização de origem, path verification, e full-path verification.

## Data Privacy

A habilidade de indivíduos controlarem a sua informação pessoal, algo que a consiga identificar só por si. Isto pode ser consultado através de roubo, pelos services providers e até por *eavesdropping*. Para isso foi criado o GDPR, que é uma lei que obriga os service providers a terem cuidado com as informações pessoais dos seus clientes. Mesmo assim, podemos ter outro tipo de seguranças, como:

- Secure Multiparty Computation;
- Não enviar os dados por caminhos não confiáveis;
- Ter cuidado com coisas simples, como sensores;
- Ataques de privacidade podem ter relação com o domínio DNS, através da identificação de tráfico;

## Security Operations

Usadas para testar e precaver problemas a nível de segurança dos sistemas e redes. Pode-se usar *monitor detection*, *logging*, *incident response status* e até *cyber threat intelligence*.

`MISP`, ou Intelligence Sharing, usa-se para desenvolver inteligência entre entidades confiáveis, partilhando suspeitas. Existe um arquivo central, o `OSINT` (Open Source Intelligence).

Pode-se também usar técnicas de *sandboxing* ou *honeypots*.