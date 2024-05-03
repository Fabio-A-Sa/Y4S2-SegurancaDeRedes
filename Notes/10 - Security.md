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