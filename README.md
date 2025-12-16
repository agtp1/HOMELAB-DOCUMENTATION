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
- Salida a internet: Para abrir puerto y salir a internet mantengo el router de mi ISP. Simplemente lo utilizo para tener conectividad a internet.(ANTIGUO)
- Ahora para salir a internet he quitado el router de mi ISP, y he puesto mi Unifi Cloud Gateway como Router para salir a internet. Mi isp es algo extraño y no me proporciona servicio a través de un usuario PPPoE, en mi caso me lo proporciona por la VLAN 20. Esto no me lo proporcionó mi ISP, me tuve que buscar la vida xD.
  
ROUTER PRINCIPAL:
- Al router le llega 1 cable a la ETH5, que es por donde salimos a internet. Seguidamente, en la ETH1, es mi puerto TRUNK del ROUTER, es decir en este puerto tengo hecha la encapsulación con las vlans para que el SWITCH PRINCIPAL, pueda gestionar y visualizar estas VLANS. 
![imagen](https://github.com/user-attachments/assets/1fc92e16-36c7-4366-adae-d117137a8fc3)


Estas son las redes actuales que están configuradas en mi red. En el puerto 1, como he dicho anteriormente están encapsuladas todas las vlans(REDES) y se conectan al puerto trunk del SWITCH PRINCIPAL.
![imagen](https://github.com/user-attachments/assets/ff9f3444-68c8-4bec-b594-f30a3de828cf)

- SERVIDOR VPN:
  ![imagen](https://github.com/user-attachments/assets/9367be48-7605-4e9e-87f5-843e0f2ff0bf)

- Servidor DHCP:
  El encargado de repartir IPs en mi RED, es el mismo Router, es decir, que no me hace falta tener un servidor DHCP dedicado, me basta con el del ROUTER.

IMPORTANTE:
Para redirijir el tráfico, no utilizo dynamic dns, ya que por suerte mi proveedor de internet, me ha ofrecido una ip PUBLICA GRATIS.

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

Por supuesto también está activado el sistema de deteccion de intrusos, que a la que visualiza un riesgo algua petición a la red lo bloquea al instante.

<img width="1471" height="897" alt="imagen" src="https://github.com/user-attachments/assets/410d404e-3928-42b8-a77b-1b142a35109f" />

<img width="1880" height="1003" alt="imagen" src="https://github.com/user-attachments/assets/d986a1b0-3583-4fe9-acea-79913efb215f" />


DASHBOARD ROUTER:
<img width="1864" height="878" alt="imagen" src="https://github.com/user-attachments/assets/e8a5a6b7-4ffd-430b-b15f-302687c40aec" />


SWITCH PRINCIPAL 
- El puerto 5 es el puerto TRUNK del SWITCH, es decir esta fisicamente conectado con un cable a mi puerto trunk del router. Es decir que el router se conecta por el puerto 1 y el switch por el puerto 5. Básicamente los puertos trunk ven todas las VLAN. En este caso el puerto 1 3 y 4 también estan en modo TRUNK, ya que es donde van conectados los dos nodos de proxmox y el AP, y me interesa que los dos nodos y el AP vean todas las vlans. En el puerto 2, que es la vlan de los CLIENTES, está conectado el switch D-LINK, ya que en este es donde van conectados los clientes. En este caso hay 4 equipos clientes conectados por cable, que son 2 PCs de sobrmesa un portatil y una TV. La camara que está dentro del "RACK", está conectada a un puerto del ROUTER, que unicamente puede ver la vlan de las CAMARAS, ya que no me quedaban mas puertos disponibles en el swtich, y en el ROUTER me sobran puertos. 
  
![imagen](https://github.com/user-attachments/assets/9d798983-26d4-475d-95d7-f11be4af2f36)

![imagen](https://github.com/user-attachments/assets/89d0eaa4-6646-49ff-b4ae-060a37001eac)

![imagen](https://github.com/user-attachments/assets/9eb96330-c431-4636-bdad-d5bdde8db123)

SERVIDORES_

PROXMOX:

PVE 1:

    MINI PC Teclast n10
    6GB ram SODIMM DDR4
    CPU Celeron N4000 2 nucleos 2 hilos 2,6 GHz
    Disco Duro Externo SSD KINGSTON 240 SATA

PVE 2:

    CPU: i5-3330
    RAM: 12GB RAM DDR3 1333 MHz
    FUENTE 450W 80 PLUS BRONZE
    DISCOS: 1 HDD 1TB, 2 HDD 500GB, 1 HDD 160GB
    TARGETA DE RED: 1 TARGETA DE RED EXTRA 1 GBPS No es un servidor muy potente pero actualmente cubre las necessidades a nivel personal.

  TRUENAS:
  Mini PC Lenovo
  
      CPU: i3 7100T
      RAM: 8GB RAM DDR4 2133 MHz
      DISCOS: 1 HDD 160 GB(S.O), 2 HDD 1000GB (RAID ESPEJO PARA LOS DATOS)


Antiguamente, tenia los dos nodos de proxmox en cluster, decidí quitarlo, porque realmente me conviene mas tenerlos separados ya que te ahorras dolores de cabeza(si tengo equipos limitados como yo). Esto no quiere decir que no recomiende usarlo, lo recomiendo al 100x100 pero aseguraros que los equipos van a estra activos 24/7, en mi caso lo quité ya que no me hacia falta tener 24/7 mis servidores activos. Ahora sí me hace falta pero por si acaso he decidido no hacer cluster.

FUNCIONES PVE1: En el nodo 1 simplemente estoy corriendo 6 contenedores y 1 VM, es el servidor mas importante del homelab:

- ADBLOCKER: Adguard

- Tengo adguard con dns encriptado dot y doh
<img width="1270" height="395" alt="imagen" src="https://github.com/user-attachments/assets/dc727d05-5eb6-4a3f-9b1a-4a70076eb840" />

<img width="546" height="150" alt="imagen" src="https://github.com/user-attachments/assets/245bff88-3255-4d06-b702-11d2c8161c45" />

<img width="439" height="434" alt="imagen" src="https://github.com/user-attachments/assets/9824a0de-911b-4eb7-b4ed-064a86eb4893" />

<img width="1300" height="926" alt="imagen" src="https://github.com/user-attachments/assets/e22a41b7-5559-453b-bdd2-df01bc21fbea" />

- DASHBOARD: Homarr
![imagen](https://github.com/user-attachments/assets/0bc7df2c-ef91-486d-810a-2856973c184d)

- PROXY: Nginx Proxy Manager
  NPM, la función que realiza en mi homelab:
  - CLOUDFLARE apunta mi dominio a MI IP PUBLICA, luego desde el router del ISP redirijo el tráfico al ROUTER UNIFI, y de ahí redirijo el puerto 80 y el 443 a la ip del NGINX proxy manager. Y NPM ya se encarga de redirijir el tráfico a los servicios locales.
    
![imagen](https://github.com/user-attachments/assets/c1e20a0c-e32a-4696-9117-9b7417f6f377)


- PASSWORD MANAGER: VaultWarden
<img width="1080" height="482" alt="imagen" src="https://github.com/user-attachments/assets/484a45db-9483-42f7-b494-c35b434ca15e" />


- MONITORIZACIÓN: UptimeKuma
![imagen](https://github.com/user-attachments/assets/e17bb57f-5432-4053-bb22-d684cc4aea8a)

- AUTOMATIZACIONES: N8N
- Estoy empezando con esta herramienta y estoy haciendo pruebas y demás.
![imagen](https://github.com/user-attachments/assets/cd5bcdd8-621c-440c-8286-7613b4861b97)

- HESTIA CP:
Sin duda una de las partes mas imprortanes del laboratorio, donde tengo mi servidor de correo electrónico y algunas páginas importantes de algun cliente.

<img width="1579" height="480" alt="imagen" src="https://github.com/user-attachments/assets/2c97861a-ec3f-461e-85a5-044ddf6994d7" />


CONSUMOS PVE 1: Aunque parezcan pocos recursos, la CPU Y la RAM, son más que suficientes para mantener activos y en correcto funcionamiento los servicios que necesito.

<img width="1398" height="389" alt="imagen" src="https://github.com/user-attachments/assets/12844a4a-ba48-4b87-bb87-8050dd88c122" />


FUNCIONES PVE 2: En el nodo 2 actualmente solo tengo corriendo Proxmox, con el contenedor crafty, para hacer servidores de minecraft. Ahora mimso le tengo todos los recursos asignados a crafty ya que en el servidor somos varias personas jugando con mods y no creo que vaya a usar nada mas.

<img width="1839" height="865" alt="imagen" src="https://github.com/user-attachments/assets/91d2cd03-e218-4cb9-ad2d-9b5566c07566" />


FUNCIONES TRUENAS

CÓPIAS DE SEGURIDAD: Mi política de copias de seguridad, es muy simple. Los contenedores que corren en el NODO 1, se hace una copia de seguridad en el espacio NFS, compartido por TrueNAS, luego estas copias se mandan a MEGA. Actualmente, tengo configurado que se realice 1 copiá de cada contenedor a principio de cada mes, ya que estos contenedores a penas sufren cambios. También realizo copias de las carpetas compartidas mas relevantes, que también son enviadas a MEGA. 
![405791494-5ea02907-65ec-4146-833f-f0530df6ffda](https://github.com/user-attachments/assets/3ed87e4c-e40d-4546-a775-e09cbb7548b9)

![405792097-6091a0c8-2d8a-4caf-bae4-7b1b9aa27a25](https://github.com/user-attachments/assets/bcb29975-3950-4c00-bc6a-7dcda8a25c94)

![405792606-768b7a18-3fc2-4962-a127-c8590f55e9ba](https://github.com/user-attachments/assets/aa3fb2fc-c1db-4f1b-9740-54933e82c19c)

HESTIA CP:
Simplemente añado los dominios y les suelo instalar un wordpress. Para realizar páginas web.

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

No dispongo de rack, pero actualmente, con los dispositivos sencillos que tengo no me hace falta, y más o menos puedo tenerlo todo medianamente organizado fácilmente.

<img width="650" height="686" alt="image" src="https://github.com/user-attachments/assets/2a6060da-b569-40fa-ac61-f016ec2ccccc" />


## UPDATES

He realizado mi homelab con lo que tengo a mano, y muy poco a poco. No es gran cosa, pero con el presupuesto que tengo cubre mis necesidades.
- Me gustaría añadir un SAI sí o sí. En mi zona no tengo cortes eléctricos. Alguna vez puede pasar pero muy de vez en cuando.
- A nivel de servidores, expandir mi almacenamiento. Me gustaria añadir dos HDD de 6 TB cada uno y formam un RAID 1. Añadirlo a TrueNAS, ya que es donde realizo los backups, los sincronizo con la nube y comparto almacenamiento en red.
- Enlaces a 10 GBPS, me encantaría tener la posibilidad de agregar enlaces a 10 GBPS entre el servidor TrueNAS y el resto de dispositivos locales.
