# **Server Weaselcloud-26445**

## **Overview**
The server provides a web environment based on the LEMP stack with a basic set of services. It processes HTTP requests through **nginx** and executes PHP scripts via **php-fpm**. **MariaDB** is used as the relational database.

The directory `/var/www/testapp` contains the welcome page files:
- `index.html`.
- Two PNG images.

## **Usage scenarios**
- A test environment (sandbox) for candidates to explore the web stack.
- Displaying a welcome page on server access.

## **Requirements**

| **Component** | **Minimum Version** |
|---------------|----------------------|
| Ubuntu        | 22.04               |
| nginx         | 1.18.0              |
| PHP           | 8.1                 |
| MariaDB       | 10.6.22             |
| Memcached     | 1.6.14              |
| Fail2Ban      | 0.11.2              |

## **Services**

### **Primary Services**

| **Service** | **Role** |
|-------------|----------|
| nginx            | Web server, HTTP request processing |
| php-fpm          | PHP code execution |
| MariaDB          | Relational database |
| Memcached        | Memory-caching system |
| Fail2Ban         | Brute-force protection |
| Postfix          | Local mail delivery agent (MDA) |
| sshd             | Remote SSH access |

### **System Services**
`cron`, `dbus`, `irqbalance`, `multipathd`, `networkd-dispatcher`,  
`getty@tty1`, `serial-getty@ttyS0`, `packagekit`, `polkit`, `rsyslog`,  
`snapd`, `systemd-journald`, `systemd-logind`, `systemd-networkd`,  
`systemd-resolved`, `systemd-timesyncd`, `systemd-udevd`, `unattended-upgrades`.

## **Component Interactions**
- **nginx** receives HTTP requests and returns static files / forwards dynamic requests to **php-fpm**.  
- **php-fpm** executes PHP scripts and connects to **MariaDB** (`127.0.0.1:3306`) and the **Memcached** cache (`127.0.0.1:11211`) when needed.  
- **Postfix** sends local system notifications.  
- **Fail2Ban** analyzes logs and blocks suspicious SSH connection attempts.

## **Open Ports**

| **Service** | **Port** | **Protocol** |
|-------------|----------|--------------|
| nginx       | 80       | TCP          |
| MariaDB     | 3306     | TCP          |
| Memcached   | 11211    | TCP          |
| sshd        | 22       | TCP          |
