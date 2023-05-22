# Configuracao basica DHCP Client

- Acesso via MAC - Feito por UDP
- Atualiza os packages da router
- Atualiza o Firmware da router
- Atualiza a senha do winbox
- Renomear interfaces
porta-wan
porta-lan

## Receber um Ip dinâmico

- Configurar o DCHP Client, para receber um endereço IP na porta que estiver entrando o LINK, Usar a ether-1
- Criar uma bridge para a lan
- Configurar o DCHP Server, e a atribuir ele a bridge que foi criada
    - Dchp Setup
    - a bridge que foi criada
- Criar ip address atribuido a bridge

> A essa altura o seu PC irá receber um endereço IP, mas não vai funcionar a internet pois não tem uma regra de NAT, você pode conferir os ips que foram distribuidos em DCHP Server > Leases
> 

Comando para zerar e renovar IP do PC (cmd):

```powershell
ipconfig /release
ipconfig /renew
ipconfig
```

- Ir em IP > Firewall > Nat
    - Chain = srcnat
    - Out. interface = ether1
        - Action = masquerade