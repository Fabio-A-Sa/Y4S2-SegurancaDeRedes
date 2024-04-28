# Transport Layer Security

Providencia:

- `Authentication`, com o cliente valida o certificado;
- `Confidentiality`, os dados passados sãpo encriptados;
- `Integrity`, pois computa um MAC e concatena à mensagem;

Isto deve-se à existência de uma pre-master key, master keys e session keys. Além disso, garante o `Perfect Forward Secrecy`, ou seja, descobrir a pre-master key não compromete os dados passados nem futuros, basta trocar.

O TLS suporta vários algoritmos, nomeadamente:

- `Key Exchange`, como RSA e outros;
- `Ciphers`, como AES ou ChaCha-20;

