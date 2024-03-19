# Firewalls and VPNs

## Firewall

Firewall é um elemento de rede que controla o tráfego de entrada, saída e local de uma aplicação. Pode ser um dispositivo comercial, um appliance de código aberto ou até mesmo software em um host para controlar o acesso ao próprio host.

O `iptables` é um firewall baseado em Linux que funciona com uma cadeia de regras aplicadas em diferentes pontos, como entrada, saída, encaminhamento, pré-roteamento e pós-roteamento. Existem um conjunto de ações, como ACCEPT, DROP, QUEUE or RETURN.

### Firewall Applications

Existem aplicações que gerenciam as regras do iptables em nome do usuário, facilitando a configuração direta das regras.

Regras Exemplificativas do iptables: Algumas regras comuns incluem definir políticas padrão para aceitar ou descartar pacotes e permitir ou bloquear conexões TCP para determinadas portas.

### Netfilter, Ebtables, Ebpf

`Netfilter` é a estrutura no kernel Linux que permite manipular pacotes de rede com comandos INPUT, OUTPUT, FWD, PRER., POSTR, enquanto `Ebtables` é equivalente ao iptables, mas para pontes Ethernet, e `eBPF` permite que código isolado seja executado no kernel para estender suas capacidades em *sandboxing*.

### Stateless vs. Stateful

Os firewalls podem operar de forma `stateless`, aplicando regras a cada pacote individualmente, ou `stateful`, lembrando pacotes relacionados anteriores. Em stateless não pode fazer duas coisas ao mesmo tempo: ou aceita DNS replies na porta X ou previne respostas não solicitadas da mesma porta. Por outro lado, o stateful tem de fazer store de mais informação, e por prevenção apenas aceita incoming packets if they belong to outbound TCP stream.

### Arquiteturas de Implantação de Firewall

- `Roteador externo`: Força o tráfego externo de entrada através do firewall.
- `Gateway de duas interfaces`: O roteador externo envia o tráfego para o host do firewall com interfaces interna e externa; a interface interna conectada à LAN interna.
- `Roteador de filtragem`, hospedeiro bastião: O roteador externo roteia todo o tráfego para o host do firewall com uma única interface.
- `Roteador interno`: Força o tráfego interno de saída através do firewall.
- `Rede filtrada`: Semelhante ao gateway de duas interfaces, exceto que a interface interna do firewall está conectada à rede DMZ, incluindo o roteador interno.
- `Firewall duplo`: Semelhante à rede filtrada, com um segundo firewall antes do roteador interno.

Existem também firewalls de nível de pacote, de nível de transporte/circuito e de aplicação. As firewalls funcionam como `egress` (proxy para internet access) ou como `ingress` (load balancing para redirecionamento TCP para diferentes internal servers).

Além disso, as Firewalls funcionam como:

- Access control;
- Content filtering and modifying;
- Content logging and caching;

## VPN

As VPNs criam redes virtuais sobre outras redes para proteger o conteúdo criptograficamente e fornecer acesso remoto seguro aos recursos da rede corporativa.

### VPN Host-to-Net

As VPNs de host para rede podem operar como túneis IP ou pontes Ethernet.

Ameaças à VPN

As ameaças à segurança da VPN incluem falhas na autenticação, vulnerabilidades de protocolo e comprometimento de chaves de usuário.

VPNs Não Convencionais

Existem VPNs não convencionais que encapsulam pacotes em protocolos não relacionados à VPN, como DNS, HTTP ou SMTP, para passar por firewalls mais restritivos.

