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

WIFI:
Ahora dispongo de 3 SSID de los cuales 2 operan únicamente en la antena de 5 GHz y la de IoT en ambas.
- Red Principal, que es donde están los miembros de casa, moviles, portatiles, tablets, etc.
- IoT, donde estan los dispotivos IoT, TV, chromechast, aspirador inteligente...
- Invitados, la cual para tener acceso internet tengo realizado un pequeño y simple HotSpot, donde antes de conectarse a mi red se tienen que autenticar para tener salida a internet.

IMPORTANTE:
- En la red IOT activo la Enhanced IoT Connectivity para que la red IoT sea lo máximo compatible con todos los dispositivos IoT aunque no cumplan con los estándares

<img width="499" alt="image" src="https://github.com/user-attachments/assets/1ece33fd-842e-41ff-b5d8-292a4fff3b02" />


![image](https://github.com/user-attachments/assets/f6ecd482-f93c-499c-a1c0-7a1f8d579754)


FIREWALL:
El router, te da una opción para hacer un firewall con reglas muy sólidas y que funciona muy pero que muy correcto. Cabe recalcar que puedes añadir o quitar reglas segun tus necesidades.

![imagen](https://github.com/user-attachments/assets/45da347a-0b33-4035-9b10-5def3387d41f)

![imagen](https://github.com/user-attachments/assets/ffb98bd7-0ca9-4cfb-a4dd-7d466bb3f1a7)

DASHBOARD ROUTER:
![imagen](https://github.com/user-attachments/assets/3e017961-16ff-4882-a786-c124d3b3b67d)


SWITCH PRINCIPAL 
- El puerto 5 es el puerto TRUNK del SWITCH, es decir esta fisicamente conectado con un cable a mi puerto trunk del router. Es decir que el router se conecta por el puerto 1 y el switch por el puerto 5. Básicamente los puertos trunk ven todas las VLAN. En este caso el puerto 1 3 y 4 también estan en modo TRUNK, ya que es donde van conectados los dos nodos de proxmox y el AP, y me interesa que los dos nodos y el AP vean todas las vlans. En el puerto 2, que es la vlan de los CLIENTES, está conectado el switch D-LINK, ya que en este es donde van conectados los clientes. En este caso hay 4 equipos clientes conectados por cable, que son 2 PCs de sobrmesa un portatil y una TV. La camara que está dentro del "RACK", está conectada a un puerto del ROUTER, que unicamente puede ver la vlan de las CAMARAS, ya que no me quedaban mas puertos disponibles en el swtich, y en el ROUTER me sobran puertos. 
  
![imagen](https://github.com/user-attachments/assets/9d798983-26d4-475d-95d7-f11be4af2f36)

![imagen](https://github.com/user-attachments/assets/89d0eaa4-6646-49ff-b4ae-060a37001eac)

![imagen](https://github.com/user-attachments/assets/9eb96330-c431-4636-bdad-d5bdde8db123)



CLUSTER PROXMOX:

NODE 1

    MINI PC Teclast n10
    6GB ram SODIMM DDR4
    CPU Celeron N4000 2 nucleos 2 hilos 2,6 GHz
    Disco Duro Externo SSD KINGSTON 240 SATA

NODE 2

    CPU: i5-3330
    RAM: 8GB RAM DDR3 1333 MHz
    FUENTE 450W 80 PLUS BRONZE
    DISCOS: 1 HDD 1TB, 2 HDD 500GB, 1 HDD 160GB
    TARGETA DE RED: 1 TARGETA DE RED EXTRA 1 GBPS No es un servidor muy potente pero actualmente cubre las necessidades a nivel personal.

IMPORTANTE:
- Al tener 2 nodos el quorum, era de mas del 50%, es decir que el cluster necesitaba mas del 50% de los nodos en funcionamiento, al tener unicamente 2 nodos, cuando apagaba el nodo2, que es donde tengo el truenas virtualizado, al rato el nodo 1 dejaba de dar servicio, es decir era inaccesicble via web, únicamente podia acceder a a el físicamente. No es recomendable quitar el quorum , pero en este caso, he decidido que es lo mejor, ya que no me interesa tener el nodo 2 siempre encendido, únicamente cuando necesito realizar backups y demás.

  PONER FOTO DEL ARCHIVO DEL QUORUM

FUNCIONES NODO 1: En el nodo 1 simplemente estoy corriendo 6 contenedores:

- ADBLOCKER: Pihole

- Tengo dos interficies de red, ya que de esta forma los de la VLAN 10 y los de la VLAN 20 (Servidores y Clientes), pueden tener de servidor DNS al PIHOLE, además los clientes de la VPN también usan de servidor DNS la 192.168.10.5(ip PIHOLE).
![imagen](https://github.com/user-attachments/assets/fadac102-66ad-41e0-9095-7bd09c3a6b4f)

![imagen](https://github.com/user-attachments/assets/4509bc77-5966-42b2-a865-92d8135fe154)

- DASHBOARD: Homarr
![imagen](https://github.com/user-attachments/assets/0bc7df2c-ef91-486d-810a-2856973c184d)

- PROXY: Nginx Proxy Manager
  NPM, la función que realiza en mi homelab:
  - CLOUDFLARE apunta mi dominio a MI IP PUBLICA, luego desde el router del ISP redirijo el tráfico al ROUTER UNIFI, y de ahí redirijo el puerto 80 y el 443 a la ip del NGINX proxy manager. Y NPM ya se encarga de redirijir el tráfico a los servicios locales.
    
![imagen](https://github.com/user-attachments/assets/c1e20a0c-e32a-4696-9117-9b7417f6f377)


- PASSWORD MANAGER: VaultWarden
![407397320-1525570c-bd01-4b54-b7e3-eea283b56343](https://github.com/user-attachments/assets/9417b2a2-56f7-426a-914b-518a0ce0c823)

- MONITORIZACIÓN: UptimeKuma
![imagen](https://github.com/user-attachments/assets/e17bb57f-5432-4053-bb22-d684cc4aea8a)

- AUTOMATIZACIONES: N8N
- Estoy empezando con esta herramienta y estoy haciendo pruebas y demás.
![imagen](https://github.com/user-attachments/assets/cd5bcdd8-621c-440c-8286-7613b4861b97)


CONSUMOS NODO 1: Aunque parezcan pocos recursos, la CPU Y la RAM, son más que suficientes para mantener activos y en correcto funcionamiento los servicios que necesito.
![imagen](https://github.com/user-attachments/assets/7fc7f270-53a8-4bae-997c-cd122d078912)

![imagen](https://github.com/user-attachments/assets/ca40befa-43ec-4112-9269-d0f088d92d27)

FUNCIONES NODO 2: En el nodo 2 actualmente solo tengo corriendo un TrueNAS, donde tengo varias carpetas compartidas vía SAMBA, también gestiono las COPIAS DE SEGURIDAD, tanto de PROXMOX, como del propio TrueNAS. En este TrueNAS, he realizado un PASSTROUGHT, de 3 discos físicos. 1 de 160GB donde simplemente está instalado el s.o, y 2 de 500GB cada uno que forman un RAID1. Dentro de TrueNAS, tengo corriendo un pequeño servidor de vídeo, concretamente Jellyfin. Donde actualmente tengo algunos capítulos de algunas series que me gustaría ver. Además, los núcleos asignados a esta máquina virtual, están en modo HOST, para que la máquina virtual utilice directamente los núcleos de la CPU. Un espacio de TrueNAS, está dedicado para las copias de seguridad de los contenedores del NODO1, este espacio está compartido mediante NFS, y está asignado al propio PROXMOX. Recientemente he añadido HESPIA CP, para administrar paginas web de "CLIENTES"(mias y de mis colegas), además de realizar un servidor de correo propio.
CONSUMOS NODO 2: 
![405790312-6e920980-fa33-4240-be01-4b6471b62c1b](https://github.com/user-attachments/assets/7741490c-ae5e-4575-9ec4-a852a49e6854)

![405790240-5818c098-8522-47f3-91f1-1e8a17752d91](https://github.com/user-attachments/assets/f17e57b9-8296-4f3b-b173-718c6b72d356)

CÓPIAS DE SEGURIDAD: Mi política de copias de seguridad, es muy simple. Los contenedores que corren en el NODO 1, se hace una copia de seguridad en el espacio NFS, compartido por TrueNAS, luego estas copias se mandan a MEGA. Actualmente, tengo configurado que se realice 1 copiá de cada contenedor a principio de cada mes, ya que estos contenedores a penas sufren cambios. También realizo copias de las carpetas compartidas mas relevantes, que también son enviadas a MEGA. 
![405791494-5ea02907-65ec-4146-833f-f0530df6ffda](https://github.com/user-attachments/assets/3ed87e4c-e40d-4546-a775-e09cbb7548b9)

![405792097-6091a0c8-2d8a-4caf-bae4-7b1b9aa27a25](https://github.com/user-attachments/assets/bcb29975-3950-4c00-bc6a-7dcda8a25c94)

![405792606-768b7a18-3fc2-4962-a127-c8590f55e9ba](https://github.com/user-attachments/assets/aa3fb2fc-c1db-4f1b-9740-54933e82c19c)

HESPIA:
Simplemente añado los dominiosM y les suelo instalar un wordpress. Para realizar páginas web.

![imagen](https://github.com/user-attachments/assets/2c7e030f-c28f-45e8-afef-55ee9b72ebc0)

PARA QUE FUNCIONE EL WEBMAIL, HAY QUE AÑADIR EL webmail.dominio.com como alieses.

![imagen](https://github.com/user-attachments/assets/fa3035b1-2bc2-4afe-986d-6ea89e6f54c6)


Para los correos simlemente añado el dominio, activo estas opciones, y para el SSL, redirijo TEMPORALMENTE el trafico del puerto 80 y el 443 a la ip del HESPIA, porque sino no se puede bajar los certificados

![imagen](https://github.com/user-attachments/assets/0725d530-d4b6-42df-8cb3-a8b0baf07d1d)

Luego para qeu funcione correctamente vemos los DNS RECORD y simplemente vamos copiando lo que nos indica en nuestro proveedor del dominio, en mi caso cloudflare.

![imagen](https://github.com/user-attachments/assets/88eb9893-f4dd-419c-a456-ddeaee30ad2f)

Si usamos cloudflare, NO TENEMOS QUE PONER LA NUBE NARNJA en los RECORDS del mail. Y tener en cuenta que tenemos que abrir estos puertos para que el correo vaya bien. En mi casa solo he abierto los de IMAP y SMTP, ya que no me hace falta el POP3.

![imagen](https://github.com/user-attachments/assets/f1e3b96a-b5b3-4aee-b311-5a25b365505c)

En mi caso los redirijo primero al unifi y del unifi a HESTIA.

![imagen](https://github.com/user-attachments/assets/1e417d77-b5b4-47e4-9efb-adea3c0e24e1)







SPEEDTEST:
- Ethernet:
  
![imagen](https://github.com/user-attachments/assets/6f7d8eeb-6179-4c3b-98e2-b910edd6432b)

- WIFI:
Aquí depende un poco de la targeta de red del cliente, si el cliente es wifi 5 y su ancho de banda és mas pequeño, llegan aproximadamente unos 300 - 350 Megas. Si el cliente(como es en este caso) es wifi 6 y si ancho de banda es mas grande podemos llegar a los 450 Megas en condiciones mas o menos óptimas. Si el cliente ya tiene wifi 6 y su ancho de banda es mucho mas grande he conseguido una velocidad de hasta 600 Megas. Con el ancho de badna de un iphone SE.

![imagen](https://github.com/user-attachments/assets/8b333643-02ec-4a02-9807-482bf28d8ed9)

CAMARAS SEGURIDAD:

    Actualmente dispongo de 2 camars de seguridad, 1 mas moderna que esta en la entrada, esta esta conectada via wifi.
    Luego tengo una "vieja" que me regalaron porque la iban a tirar y decidí aprovecharla mediante el software YOOSE, que es un software genérico para cámaras, esta camara la tengo dentro del rack mas que nada para toquetear un poco.

## "RACK"

No dispongo de rack, pero actualmente, con los dispositivos sencillos que tengo no me hace falta, y más o menos puedo tenerlo todo medianamente organizado fácilmente.ç

![imagen](https://github.com/user-attachments/assets/fbafbdcd-ae2a-4f92-a7f0-09e6bf5dada5)


## UPDATES

He realizado mi homelab con lo que tengo a mano, y muy poco a poco. No es gran cosa, pero con el presupuesto que tengo cubre mis necesidades.
- Me gustaría añadir un SAI sí o sí. En mi zona no tengo cortes eléctricos. Alguna vez puede pasar pero muy de vez en cuando.
- A nivel de servidores, expandir mi almacenamiento. Me gustaria añadir dos HDD de 6 TB cada uno y formam un RAID 1. Añadirlo a TrueNAS, ya que es donde realizo los backups, los sincronizo con la nube y comparto almacenamiento en red.
- Enlaces a 10 GBPS, me encantaría tener la posibilidad de agregar enlaces a 10 GBPS entre el servidor TrueNAS y el resto de dispositivos locales.
