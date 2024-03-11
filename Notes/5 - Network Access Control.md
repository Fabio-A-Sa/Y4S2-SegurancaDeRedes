# Network Access Control

## Internal vs. External access

Através da criação de uma `NAT` (que não deixa IPs internos serem mapeados para o exterior) ou `Firewalls` (que filtram portas e IPs provenientes do exterior).

Aqui o **Threat Model** é expandido para os agentes externos apenas, garantindo que pelo menos a rede interna é segura. A rede pode depois ser subdividida entre várias intranets.

## Physical Access

Através de portas ou networks não usadas e portanto não rastreáveis. Pode haver também restrição a nível do IP/MAC, mas seria vulnerável a spoofing.

## Same LAN access

Se o atacante tiver acesso à Ethernet layer. Então, diferentes users, com diferentes roles, devem estar em LANs diferentes, usando sub-networks. No entanto, por motivos de carga, não devemos ter uma VLAN por cada utilizador.

## IP Routing Access

Devemos restringir routing all-to-all, permitindo criar uma lista de controlo de acessos de tráfico entre IPs addresses.

## Service Access

Os serviços às vezes são vulneráveis a ataques com UDP e TCP. Pode ser prevenido com Router ACLs ou Firewalls, a explorar mais à frente.

## End-user device and VM isolation

O próprio end-user pode ser comprometido, pelo que é importante ter uma network de quarentena, hypervisors, VMs e treinamento pessoal dos utilizadores.

## Zero Trust Security

The Zero Trust security model ensures that no user or device, whether inside or outside the organization's network, is automatically trusted, emphasizing continuous verification and validation of access requests Characteristics:

- `Continuous Verification`: Users and devices are consistently authenticated and authorized, with adaptive multi-factor authentication;

- `Intelligent Access Limitation`: Access to resources is restricted based on user roles and device configurations, ensuring functional efficiency;

- `Dynamic Adaptation`: The model emphasizes continuous improvement and adaptation to evolving threats, supported by regular updates and feedback systems;