# HOMELAB-DOCUMENTATION
## ELEMENTOS DE RED
ROUTER:
- [Unifi Cloud Gateway Ultra]([url](https://www.pccomponentes.com/mikrotik-hap-ac2-punto-de-acceso1167mbps-dual-band-poe?utm_source=366479&utm_medium=afi&utm_campaign=es-go.kelkoogroup.net&sv1=affiliate&sv_campaign_id=366479&awc=20981_1736207023_47a5b89131152021a64a39caa9ae412f&utm_term=deeplink&utm_content=62A001JGZ01FAS3PDVMEC6KPH2GEST))
  
![image](https://github.com/user-attachments/assets/13598832-79d6-4616-bf9c-e89ac4aff423)


SWITCH PRINCIPAL
- [Mikrotik RB260GS ]([url](https://www.pccomponentes.com/mikrotik-rb260gs-switch-5-puertos-gigabit-1-sfp))
  
![image](https://github.com/user-attachments/assets/53819aa6-65ea-4c46-bd8c-631e6921c3e4)

SWITCH CLIENTES:
- [D-LINK  DGS-108]([url](https://www.pccomponentes.com/d-link-dgs-108-switch-8-puertos-10-100-1000mbps))
  
![image](https://github.com/user-attachments/assets/c9d015b1-5afd-495b-b259-84c7b7ed6fb8)

PUNTO DE ACCESO:
- [UAP-AC-LITE ]([url](https://www.pccomponentes.com/mikrotik-rb260gs-switch-5-puertos-gigabit-1-sfp))

![UAP-AC-LITE](https://github.com/user-attachments/assets/a72c7ca3-1c09-4ed9-822a-3670096a6724)


DISTRIBUCIÓN RED:
- Salida a internet: Para abrir puerto y salir a internet mantengo el router de mi ISP. Simplemente lo utilizo para tener conectividad a internet.
  
ROUTER PRINCIPAL:
- Al router le llega 1 cable a la ETH5, que es por donde salimos a internet. Seguidamente, en la ETH1, es mi puerto TRUNK del ROUTER, es decir en este puerto tengo hecha la encapsulación con las vlans para que el SWITCH PRINCIPAL, pueda gestionar y visualizar estas VLANS. 
![imagen](https://github.com/user-attachments/assets/1fc92e16-36c7-4366-adae-d117137a8fc3)


Estas son las redes actuales que están configuradas en mi red. En el puerto 1, como he dicho anteriormente están encapsuladas todas las vlans(REDES) y se conectan al puerto trunk del SWITCH PRINCIPAL.
![imagen](https://github.com/user-attachments/assets/ff9f3444-68c8-4bec-b594-f30a3de828cf)

- SERVIDOR VPN:
  ![imagen](https://github.com/user-attachments/assets/9367be48-7605-4e9e-87f5-843e0f2ff0bf)

- Servidor DHCP:
  El encargado de repartir IPs en mi RED, es el mismo Router, es decir, que no me hace falta tener un servidor DHCP dedicado, me basta con el del ROUTER.



SWITCH PRINCIPAL 
- El puerto 5 es el puerto TRUNK del SWITCH, es decir esta fisicamente conectado con un cable a mi puerto trunk del router. Es decir que el router se conecta por el puerto 1 y el switch por el puerto 5. Básicamente los puertos trunk ven todas las VLAN. En este caso el puerto 3 y 4 también estan en modo TRUNK, ya que es donde van conectados los dos nodos de proxmox, y me interesa que los dos nodos vean ambas vlans. Y el puerto 1, esta assignado la vlan 30, ya que aquí es donde se conecta la camara de seguridad.
![407395227-5df0c862-8a06-465d-aee2-8e3bccc3616d](https://github.com/user-attachments/assets/b8b0ed89-2be8-464b-a786-c05ac1f1cb03)

![407395327-345e2a83-48c4-4513-899b-df8f4d06f2a8](https://github.com/user-attachments/assets/79c1d07a-ffef-4221-a197-abd371816b64)

![407395387-8d9b50f6-19a2-41df-81e5-f33f88a25fce](https://github.com/user-attachments/assets/ee5bbfdd-997f-4b28-9fa5-107f902c3c55)

