# Configuración Seguridad Wazuh

---

## **228584: Ensure nftables is not installed with iptables**
Para garantizar que `nftables` no esté instalado junto con `iptables`, ejecuta el siguiente comando:

```bash
sudo apt purge nftables
```

---

## **28590: Ensure auditd is installed**
Asegúrate de que el paquete `auditd` esté instalado:

```bash
sudo apt-get install auditd
```

---

## **28594: Ensure audit log storage size is configured**
Configura el tamaño de almacenamiento de los logs de auditoría a 50 MB:

```bash
sudo sed -i 's/^max_log_file.*/max_log_file = 50/' /etc/audit/auditd.conf && sudo systemctl restart auditd
```

---

## **28561: Ensure Samba is not installed**
Para eliminar el paquete Samba, ejecuta:

```bash
sudo apt purge samba
```

---

## **28550: Ensure ntp is enabled and running**
Habilita y arranca el servicio NTP:

```bash
sudo systemctl unmask ntp.service && sudo systemctl --now enable ntp.service
```

---

## **28570: Ensure telnet client is not installed**
Elimina el cliente Telnet, si está instalado:

```bash
sudo apt purge telnet
```

---

## **28566: Ensure rsync service is either not installed or masked**
Desinstala o desactiva el servicio `rsync`:

```bash
sudo apt purge rsync 
sudo systemctl stop rsync 
sudo systemctl mask rsync
```

---

## **28526: Ensure AIDE is installed**
Instala el paquete `AIDE` para la detección de intrusos:

```bash
sudo apt update && sudo apt install -y aide aide-common
```

---

## **28583: Ensure iptables packages are installed**
Instala y configura las reglas de `iptables`:

```bash
sudo apt-get install iptables-persistent 
sudo iptables-save > /etc/iptables/rules.v4 
sudo ip6tables-save > /etc/iptables/rules.v6
```

---

## **28614: Ensure systemd-journal-remote is installed**
Instala el paquete `systemd-journal-remote` para gestionar registros remotos:

```bash
sudo apt update && sudo apt install -y systemd-journal-remote
```

