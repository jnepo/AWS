# Laboratorio IP Tables

### ✅ Agregar reglas para no cortar el acceso a la instancia EC2

#### Permitir tráfico loopback
    sudo iptables -A INPUT -i lo -j ACCEPT

#### Permitir conexiones ya establecidas o relacionadas
    sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#### Permitir SSH
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

### 🚫 Cambiar las políticas por defecto a DROP
    sudo iptables -P INPUT DROP
    sudo iptables -P FORWARD DROP
    sudo iptables -P OUTPUT ACCEPT

### ✅ Permitir tráfico entrante al puerto 80 (HTTP)
    sudo iptables -A INPUT -p tcp --dport 80 -m conntrack --ctstate NEW -j ACCEPT

### ✅ Permitir tráfico de ping
    sudo iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
