# Manual Técnico Practica 1

- **Carnet 202106538**

## 1. Configuración

### Configuración de routers
### Router 1


    enable
    configure terminal
    interface s1/0
    ip address 10.0.0.1 255.255.255.252 
    no shutdown
    exit
    
    interface fa0/0
    ip address 182.168.1.2 255.255.255.248
    no shutdown
    exit
    
    interface fa0/1
    ip address 182.168.2.2 255.255.255.248
    no shutdown
    exit

---

### Router 2 
    enable
    configure terminal
    interface fa0/0
    ip address 182.168.1.1 255.255.255.248
    no shutdown
    exit
    
    interface fa0/1
    ip address 182.168.0.2 255.255.255.0
    standby 1 ip 182.168.0.1
    standby 1 priority 120
    standby 1 preempt
    no shutdown
#### configurado como router activo
------
### Router 6
    enable
    configure terminal
    interface fa0/0
    ip address 182.178.1.2 255.255.255.248
    no shutdown
    exit
    
    interface fa0/1
    ip address 182.178.0.2 255.255.255.0
    standby 2 ip 182.178.0.1
    standby 2 priority 120
    standby 2 preempt
    no shutdown
    exit
#### configurado como router activo
---

### Configuración de switches
### SW1
    enable
    configure terminal
    interface range fa0/3-4
#### conectar grupo del switch con el switch 0
    channel-group 1 mode auto
    exit
    
    interface port-channel 1
    switchport mode trunk

#### para ver pagp configurado en el switch
    show etherchannel

----
### SW3 (misma configuración para SW2)
    enable
    configure terminal
    interface range fa0/3-4
    channel-group 2 mode active
    exit
    
    interface port-channel 2
    switchport mode trunk
    exit

    exit
#### para ver pagp configurado en el switch
    show etherchannel

----
### Configuración de VPCs
### VPC 11
- Ip Address: 182.168.0.4
- Subnet Mask: 255.255.255.0
- Default Gateway: 182.168.0.1

### VPC 14
- Ip Address: 182.178.0.5
- Subnet Mask: 255.255.255.0
- Default Gateway: 182.178.0.1
