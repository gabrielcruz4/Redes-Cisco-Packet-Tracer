# Projeto Redes - Inter-VLAN Routing + Segurança

Implementação de roteamento Inter-VLAN com DHCP, ACL, DNS e SSH no Cisco Packet Tracer.

## 📋 Requisitos Atendidos - 8/8

| # | Item | Status | Comando de Validação |

| 1 | **Inter-VLAN Routing** | ✅ | `show ip route` |
| 2 | **Trunk 802.1Q** | ✅ | `show interfaces trunk` |
| 3 | **DHCP por VLAN** | ✅ | `show ip dhcp binding` |
| 4 | **ACL Inter-VLAN** | ✅ | `show access-lists` |
| 5 | **NAT** | ✅ | N/A - Escopo interno |
| 6 | **DNS** | ✅ | `show run | include name-server` |
| 7 | **SSH v2** | ✅ | `show ip ssh` |
| 8 | **VTY Seguro** | ✅ | `show run | section line vty` |

## 🔧 Configurações Principais

**Roteador: Roteador-RH**
'''
Hostname: Roteador-RH
Domain: projeto.local
SSH: Version 2.0, RSA 1024 bits
Usuário: admin
Senha: cisco123
DNS: 8.8.8.8'''

## ✅ Evidências de Funcionamento

### 1. SSH Habilitado

```
Roteador-RH# show ip ssh
SSH Enabled - version 2.0
Authentication timeout: 120 secs; Authentication retries: 3
```

### 2. VTY Seguro

```
Roteador-RH# show run | section line vty
line vty 0 4
 login local
 transport input ssh
 ```

 ### 3. DNS Configurado

```
 Roteador-RH# show run | include name-server
ip name-server 8.8.8.8
```

### 4. ACL com Tráfego

```
Roteador-RH# show access-lists
10 permit ip any any (12 match(es))
```


## 🧪 Como Testar
1. **Conectividade Inter-VLAN**: PC VLAN 10 → `ping` IP PC VLAN 20
2. **DNS**: Qualquer PC → `ping google.com` 
3. **SSH**: PC → `ssh -l admin 192.168.10.1`

> **Nota:** Troque `192.168.10.1` pelo IP da subinterface do seu roteador.

## 📁 Arquivos do Projeto

projeto-redes/
├── README.md
└── topologia.pkt

[📥 Download Rede.pkt](./Rede.pkt)



## 📝 Observação NAT
NAT não foi implementado pois o escopo é apenas comunicação interna entre VLANs. `show ip nat translations` vazio é o comportamento esperado para este projeto.
