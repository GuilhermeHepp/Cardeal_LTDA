O plano de endereçamento, que é a tabela de IPs de todas as máquinas. Decida isso antes de configurar qualquer coisa, porque DHCP, DNS e os serviços dependem dele. Esta é a proposta, que você pode ajustar se quiser:

Máquina	Função	Interface	Endereço
VM1	Gateway + DHCP	LAN (Rede Interna)	192.168.50.1
VM1	Gateway + DHCP	WAN (NAT)	automático (DHCP do VirtualBox)
VM2	Web (Apache) + Arquivos (Samba)	LAN	192.168.50.10
VM3	DNS (BIND) + E-mail (Postfix/Dovecot)	LAN	192.168.50.11
Clientes	Hosts da rede	LAN	192.168.50.100 a 192.168.50.200 (DHCP)

Dados gerais da rede:

Rede: 192.168.50.0/24, máscara 255.255.255.0
Gateway padrão: 192.168.50.1
Servidor DNS entregue pelo DHCP: 192.168.50.11
Domínio: cardeal.local

Registros que o DNS vai ter:

www.cardeal.local aponta para 192.168.50.10
mail.cardeal.local aponta para 192.168.50.11