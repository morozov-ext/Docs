# **Weaselcloud-26445 Server**

## **Overview**
The server provides a web environment based on the LEMP stack with a basic set of services. It handles HTTP requests through **nginx** and executes PHP scripts via **PHP-FPM**. **MariaDB** is used as the relational database.

The directory `/var/www/testapp` contains the welcome page files:
- `index.html`.
- Two PNG images.

## **Usage scenarios**
- As a test environment (sandbox) for candidates to explore the web stack.
- For displaying a welcome page on server access.

## **Requirements**

- Ubuntu >= 22.04.  
- nginx >= 1.18.0.  
- PHP >= 8.1.  
- MariaDB >= 10.6.22.  
- Memcached >= 1.6.14.  
- Fail2Ban >= 0.11.2.

## **Primary Services**

| **Active Service** | **Role** |
|-------------|----------|
| nginx            | Web server, HTTP request processing |
| PHP-FPM          | PHP code execution |
| MariaDB          | Relational database |
| Memcached        | Memory-caching system |
| Fail2Ban         | Brute-force protection |
| Postfix          | Local mail delivery agent (MDA) |
| sshd             | Remote SSH access |

## **Component Interactions**
- **nginx** receives HTTP requests and returns static files / forwards dynamic requests to **PHP-FPM**.  
- **PHP-FPM** executes PHP scripts and connects to **MariaDB** (`127.0.0.1:3306`) and the **Memcached** cache (`127.0.0.1:11211`) when needed.  
- **Postfix** sends local system notifications.  
- **Fail2Ban** analyzes logs and blocks suspicious SSH connection attempts.

## **Open Ports**

| **Service** | **Port** | **Protocol** |
|-------------|----------|--------------|
| nginx       | 80       | TCP          |
| MariaDB     | 3306     | TCP          |
| Memcached   | 11211    | TCP          |
| sshd        | 22       | TCP          |
