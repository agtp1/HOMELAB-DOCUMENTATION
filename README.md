# HOMELAB-DOCUMENTATION
## ELEMENTOS DE RED
ROUTER:
- [Unifi Cloud Gateway Ultra]([url](https://www.pccomponentes.com/mikrotik-hap-ac2-punto-de-acceso1167mbps-dual-band-poe?utm_source=366479&utm_medium=afi&utm_campaign=es-go.kelkoogroup.net&sv1=affiliate&sv_campaign_id=366479&awc=20981_1736207023_47a5b89131152021a64a39caa9ae412f&utm_term=deeplink&utm_content=62A001JGZ01FAS3PDVMEC6KPH2GEST))
  
[![image](https://github.com/user-attachments/assets/7798fc39-5f98-4b87-86a9-4a8ef039f4ff)](https://www.bing.com/aclick?ld=e89V5qNcWiCBgavLCl4o1nvzVUCUxKAVuLuyLk37DPS1Kj3ypIIbVKc0gFHNww5UFxi5I8WsvM8USPE3bFhMaFEHtqxUPToK3tQR3XUuEjD4sMxoh-7YQYiBEc5VfSkpRSeQZHst5SV3ZkHAs5LkXACXZT7g95SWNXtr2mll1MUTFV0sGK&u=aHR0cHMlM2ElMmYlMmZnby50d2VuZ2EuZXMlMmZ0byUzZnMlM2QxMDM1NzMzNyUyNnAxJTNkMDglMjZnYXAlM2QlMjZnYXQlM2RwbGFfYmluZyUyNmFhZ2lkJTNkMTE1NTU4NzE4NDIyMjgzMyUyNmFjaWQlM2QzODU0OTc4NDUlMjZhdGlkJTNkcGxhLTQ1NzU4MjM4MDQ2MjA5MzclMjZhYWRpZCUzZCUyNm1jb2lkJTNkNzgyNDI4ODQzOTcwMDEyNTAyMyUyNmFwcGlkJTNkNDU3NTgyMzgwNDYyMDkzNyUyNmdkJTNkYyUyNm1jaWQlM2Q5ODY5NCUyNmdjbGlkJTNkMDAyYmRiY2EyMjc3MWMzN2E1OWZiYzEzN2U4YzkzMGMlMjZzb3VyY2UlM2RiaW5nJTI2dXJsJTNkaHR0cHMlMjUzQSUyNTJGJTI1MkZ3d3cud29ydGVuLmVzJTI1MkZwcm9kdWN0b3MlMjUyRm90cm9zJTI1MkZjbG91ZC11YmlxdWl0aS11bmlmaS1nYXRld2F5LXVsdHJhLXVjZy11bHRyYS1NUktFQU4tMDgxMDA4NDY5NTIwMyUyNm1zY2xraWQlM2QwMDJiZGJjYTIyNzcxYzM3YTU5ZmJjMTM3ZThjOTMwYw&rlid=002bdbca22771c37a59fbc137e8c930c&ntb=1)

SWITCH PRINCIPAL
- [Mikrotik RB260GS ]([url](https://www.pccomponentes.com/mikrotik-rb260gs-switch-5-puertos-gigabit-1-sfp))
  
![image](https://github.com/user-attachments/assets/53819aa6-65ea-4c46-bd8c-631e6921c3e4)

SWITCH CLIENTES:
- [D-LINK  DGS-108]([url](https://www.pccomponentes.com/d-link-dgs-108-switch-8-puertos-10-100-1000mbps))
  
![image](https://github.com/user-attachments/assets/c9d015b1-5afd-495b-b259-84c7b7ed6fb8)

DISTRIBUCIÓN RED:
- Salida a internet: Para abrir puerto y salir a internet mantengo el router de mi ISP. Simplemente lo utilizo para tener conectividad a internet.
ROUTER PRINCIPAL:
- Al router le llega 1 cable a la ETH1, que es por donde salimos a internet. Seguidamente, en la ETH5, es mi puerto TRUNK del ROUTER, es decir en este puerto tengo hecha la encapsulación con las vlans para que el SWITCH PRINCIPAL, pueda gestionar y visualizar estas VLANS. También he metido la ETH5, en un BRIDGE, a este BRIDGE. le he asignado una IP y he creado un DHCP, para que el SWITCH PRINCIPAL, reciba una IP.
- Para la parte wifi, de momento el router está funcionando como ap, ya que actualmente no dispongo de un ap. Tengo configurada las dos antenas, tanto la de 2,4 GHz como la de 5 Ghz. Disponen las 2 del mismo SSID, de esta forma, el propio cliente, elegirá a que banda conectarse dependiendo de la situación donde esté el cliente.
