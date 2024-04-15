# Authentication Protocols

Depois da autenticação do serviço ou cliente, autorização será dada para um serviço. A autenticação pode ser por via de *secrets* ou *biometrics*. 

- Passwords podem ser descobertas por brute force;
- Mesmo cifradas na base de dados, podem estar comprometidas com `Rainbow tables`;
- Por isso usa-se `salt`;

**Eavesdropping** acontece quando se tenta interceptar dados durante as ligações. Os dados não devem ser passados por simples hashes, mas sim 