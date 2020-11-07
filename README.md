# Redes1-Practica5_Grupo12
## 201700326

## Numero de host para las topologias

| Departamento | Cantidad de host |
| -------------|:----------------:|
| Profesores   | 42               |
| Estudiantes  | 72               |
| Invitados    | 22               |

## Definición de las redes por vlsm

| Direccion de Red | Primera Direccion Asignable | Ultima Direccion Asignable | Direccion de Broadcast |
|:-------------:|:-------------:|:-------------:|:-------------:| 
| 192.168.0.0/25 | 192.168.0.1 | 192.168.0.126 | 192.168.0.127 |
| 192.168.0.128/26 | 192.168.0.129 | 192.168.0.190 | 192.168.0.191 |

<h2>Topologia 1</h2>

![image](https://i.imgur.com/q3akhjq.png)

## Configuracion

### Creación de VLANS

#### Comandos:
- conf t
- vlan {numero}
- name {nombre}
- end
  
Podemos ver en el ESW con vl, si estan todas las vlans creadas

![image](https://i.imgur.com/HUKYSuD.png)

### Configuración de puertos
- conf t
- interface {interface}
- switchport mode trunk
- end

Verificamos con "sh interfaces status"

![image](https://i.imgur.com/WXK3Vhf.png)

En el switch de capa dos, con la ayuda de la GUI configuramos modo access y trunk

![image](https://i.imgur.com/ajivx2a.png)

### Gateway VLANS

Como tenemos 2 vlans, se procede a hacer subinterfaces

#### Comandos:
- conf t
- interface {nombre}
- ip address {ip} {mascara de subred}
- end

Verificamos con "sh ip interface brief"

![image](https://i.imgur.com/VhFrvpR.png)

### Ruteo estatico
Para poder acceder a la topologia 2, se debe aprender las redes que no ve el router

#### Comandos:
- conf t
- ip route {ip de la red} {mascara de la red} {ip de la interfaz}
- end

Para corroborar esto, se debe hacer ping desde un cliente a la otra topologia

![image](https://i.imgur.com/IRpZepG.png)

