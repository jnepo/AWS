# Laboratorio IP Tables

### ✅ Paso 1: Agregás primero las reglas necesarias para no cortarte el acceso

#### Permitir tráfico loopback
    sudo iptables -A INPUT -i lo -j ACCEPT

#### Permitir conexiones ya establecidas o relacionadas
    sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#### Permitir SSH
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

### 🚫 Paso 2: Cambiar las políticas por defecto a DROP

    sudo iptables -P INPUT DROP
    sudo iptables -P FORWARD DROP
    sudo iptables -P OUTPUT ACCEPT

