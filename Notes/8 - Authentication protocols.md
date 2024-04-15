# Authentication Protocols

Depois da autenticação do serviço ou cliente, autorização será dada para um serviço. A autenticação pode ser por via de *secrets* ou *biometrics*. 

- Passwords podem ser descobertas por brute force;
- Mesmo cifradas na base de dados, podem estar comprometidas com `Rainbow tables`;
- Por isso usa-se `salt`;

**Eavesdropping** acontece quando se tenta interceptar dados durante as ligações. Os dados não devem ser passados por simples hashes, mas sim por SSH.

**SSH** permite enviar plaintext por um canal cifrado, comunicando de forma segura. 

Ainda assim é importante ter um método de autenticação por challenge (*handshake authentication protocol*), de modo a restringir hipótese de autenticadores maliciosos, usando também chaves assimétricas. Pode ser conseguido através de Smart Cards, que contém as keys públicas e privadas necessárias, ou através de Multifactor Authentication.

**Single Sign-ON**, ou SSO, é a técnica usada para acessar um serviço ou um conjunto de serviços. Permite acesso sem registar o utilizador ou fazer check de passwords sempre em todos os websites.