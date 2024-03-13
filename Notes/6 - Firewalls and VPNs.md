# Firewalls and VPNs

## Firewall

Firewall é um elemento de rede que controla o tráfego de entrada, saída e local de uma aplicação. Pode ser um dispositivo comercial, um appliance de código aberto ou até mesmo software em um host para controlar o acesso ao próprio host.

O `iptables` é um firewall baseado em Linux que funciona com uma cadeia de regras aplicadas em diferentes pontos, como entrada, saída, encaminhamento, pré-roteamento e pós-roteamento. Existem um conjunto de ações, como ACCEPT, DROP, QUEUE or RETURN.

### Firewall Applications

Existem aplicações que gerenciam as regras do iptables em nome do usuário, facilitando a configuração direta das regras.

Regras Exemplificativas do iptables: Algumas regras comuns incluem definir políticas padrão para aceitar ou descartar pacotes e permitir ou bloquear conexões TCP para determinadas portas.

### Netfilter, Ebtables, Ebpf

Netfilter é a estrutura no kernel Linux que permite manipular pacotes de rede, enquanto Ebtables é equivalente ao iptables, mas para pontes Ethernet, e eBPF permite que código isolado seja executado no kernel para estender suas capacidades.

### Stateless vs. Stateful

Os firewalls podem operar de forma stateless, aplicando regras a cada pacote individualmente, ou stateful, lembrando pacotes relacionados anteriores.

Arquiteturas de Implantação de Firewall

Existem várias arquiteturas de implantação de firewall, incluindo roteador externo, gateway de várias interfaces, bastião, entre outros.

Outros Tipos de Firewall

Existem também firewalls de nível de pacote, de nível de transporte/circuito e de aplicação.

VPN

As VPNs criam redes virtuais sobre outras redes para proteger o conteúdo criptograficamente e fornecer acesso remoto seguro aos recursos da rede corporativa.

Tipos de VPN Host-to-Net

As VPNs de host para rede podem operar como túneis IP ou pontes Ethernet.

Ameaças à VPN

As ameaças à segurança da VPN incluem falhas na autenticação, vulnerabilidades de protocolo e comprometimento de chaves de usuário.

VPNs Não Convencionais

Existem VPNs não convencionais que encapsulam pacotes em protocolos não relacionados à VPN, como DNS, HTTP ou SMTP, para passar por firewalls mais restritivos.

