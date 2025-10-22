# Network-Infrastructure-Lab-Cisco

# Network Infrastructure Lab 🚀

Implementação completa de infraestrutura de rede corporativa simulada no Cisco Packet Tracer, incluindo segmentação por VLANs, roteamento inter-VLAN, redundância, alta disponibilidade e segurança.

## 📋 Índice

- [Visão Geral](#visão-geral)
- [Topologia da Rede](#topologia-da-rede)
- [Tecnologias Implementadas](#tecnologias-implementadas)
- [Configurações Principais](#configurações-principais)
- [Estrutura de VLANs](#estrutura-de-vlans)
- [Redundância e Alta Disponibilidade](#redundância-e-alta-disponibilidade)
- [Conectividade Internet](#conectividade-internet)
- [Como Utilizar](#como-utilizar)
- [Contribuições](#contribuições)

## 🎯 Visão Geral

Este projeto simula uma infraestrutura de rede corporativa completa, demonstrando boas práticas de segmentação, redundância e segurança. A implementação inclui múltiplos switches, roteadores, servidores e estações de trabalho organizadas em VLANs funcionais.

## 🌐 Topologia da Rede
[INTERNET] ←→ [NAT Router] ←→ [ISP Router] ←→ [CORE Switches] ←→ [Access Switches] ←→ [Users/Servers]
↑
[Servidor WEB]


## 🔧 Tecnologias Implementadas

### ⚡ Camada de Access
- **Switches 2960**: Portas Gigabit para acesso de usuários
- **VLANs**: Segmentação por departamentos
- **STP**: Prevenção de loops na rede

### 🔄 Camada de Core
- **Switches 3650/3050**: Roteamento inter-VLAN
- **HSRP**: Gateway redundante
- **EtherChannel**: Agregação de links
- **IP Routing**: Roteamento estático e dinâmico

### 🌍 Conectividade
- **NAT**: Tradução de endereços
- **Roteamento Estático**: Controle de tráfego
- **ACLs**: Filtragem básica

## ⚙️ Configurações Principais

### VLANs Implementadas
```bash
VLAN 100: Financeiro - 192.168.0.0/24
VLAN 200: RH         - 192.168.1.0/24  
VLAN 300: NOC        - 192.168.2.0/24
VLAN 400: DC         - 10.0.0.0/24
VLAN 500: ISP        - 10.10.10.0/24
```


## ⚙️ Configuração HSRP (Gateway Redundante)
```bash
# CORE1 (Ativo)
interface vlan 100
 ip address 192.168.0.9 255.255.255.0
 standby 100 ip 192.168.0.1
 standby 100 priority 120
 standby 100 preempt
```

# CORE2 (Standby)
```bash
interface vlan 100  
 ip address 192.168.0.10 255.255.255.0
 standby 100 ip 192.168.0.1
```

## PortChannel para Redundância
# CORE1
```bash
interface range gigabitEthernet 1/0/1-2
 channel-group 1 mode active
``` 

## CORE2
```bash
interface range gigabitEthernet 1/0/1-2
 channel-group 1 mode passive
``` 
## NAT e Filtragem
```bash
# Configuração NAT
interface g6/0
 ip nat inside
interface g7/0  
 ip nat outside
access-list 1 permit any
ip nat inside source list 1 interface g7/0
```
🚀 Funcionalidades Avançadas
✅ Implementado
Segmentação completa por VLANs

Roteamento inter-VLAN

Gateway redundante com HSRP

Agregação de links com EtherChannel

Prevenção de loops com STP

Conectividade internet com NAT

Servidor DHCP centralizado

Servidor WEB

🔄 Em Desenvolvimento
Autenticação 802.1X

Monitoramento com SNMP

QoS para voIP

VPN Site-to-Site

```text
Network-Infrastructure-Lab/
│
├── Configurations/
│   ├── Core-Switches/
│   ├── Access-Switches/
│   └── Routers/
│
├── Documentation/
│   ├── Network-Diagram.pdf
│   ├── IP-Scheme.md
│   └── VLAN-Mapping.md
│
└── Packet-Tracer-Files/
    ├── Final-Implementation.pkt
    └── Step-by-Step-Labs/
```

<div align="center">
⭐️ Se este projeto foi útil, deixe uma estrela no repositório! ⭐️

</div> ```
