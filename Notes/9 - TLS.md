# Transport Layer Security

Providencia:

- `Authentication`, com o cliente valida o certificado;
- `Confidentiality`, os dados passados sãpo encriptados;
- `Integrity`, pois computa um MAC e concatena à mensagem;

Isto deve-se à existência de uma pre-master key, master keys e session keys. Além disso, garante o `Perfect Forward Secrecy`, ou seja, descobrir a pre-master key não compromete os dados passados nem futuros, basta trocar.

O TLS suporta vários algoritmos, nomeadamente:

- `Key Exchange`, como RSA e outros;
- `Ciphers`, como AES ou ChaCha-20;

O TLS roda em cima da camada de transporte e abaixo da aplicação em si. Recorre a fragmentos, com no máximo 2^24 bytes de informação cada, todos os pacotes são enviados com um MAC e encriptação através de uma chave de sessão pré acordada entre os endpoints. Principais etapas:

- `Handshake`, onde há o conhecimento dos endpoints e correspondente troca de chaves públicas, certificados e chaves de sessão;
- `Protocol Negotiation`, onde cada endpoint apresenta o seu meio de comunicação preferido;

O TLS está na base do HTTPS.