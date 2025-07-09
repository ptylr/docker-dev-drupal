```
        __          .__
_______/  |_ ___.__.|  |_______
\____ \   __<   |  ||  |\_  __ \
|  |_> >  |  \___  ||  |_|  | \/
|   __/|__|  / ____||____/__|
|__|         \/

https://ptylr.com
https://www.linkedin.com/in/ptylr/
```
# 🧱 Drupal 11 + MariaDB + Ngrok (Docker Compose)

A lightweight local development environment for **Drupal 11**, backed by **MariaDB**, and exposed securely via **Ngrok**.

> 🔗 GitHub: [https://github.com/ptylr/docker-dev-drupal](https://github.com/ptylr/docker-dev-drupal)

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/ptylr/docker-dev-drupal.git
cd docker-dev-drupal
```

### 2. Configure Environment Variables

Copy the example files:

```bash
cp .env.example .env
cp ngrok.yml.example ngrok.yml
```

Then edit `.env` to define your database credentials:

```ini
# .env
DRUPAL_DB_HOST=db:3306
DRUPAL_DB_NAME=drupal
DRUPAL_DB_USER=drupal
DRUPAL_DB_PASSWORD=drupal

MYSQL_DATABASE=drupal
MYSQL_USER=drupal
MYSQL_PASSWORD=drupal
MYSQL_ROOT_PASSWORD=rootpass
```

And edit `ngrok.yml` to include your Ngrok authtoken and domain:

```yaml
# ngrok.yml
version: 2
authtoken: <your-ngrok-authtoken>
tunnels:
  drupal:
    addr: drupal:80
    proto: http
    domain: <your-ngrok-subdomain>.ngrok-free.app
```

---

## ▶️ Start the Stack

```bash
docker-compose up --build
```

This will:

- Start Drupal 11 using the official `drupal:11-apache` image
- Launch a MariaDB 10.6 database container
- Expose Drupal publicly via Ngrok using your configured domain

---

## 🌐 Access Drupal

- **Ngrok:** `https://<your-ngrok-subdomain>.ngrok-free.app`

---

## 🗃 File Structure

```
.
├── docker-compose.yml
├── .env / .env.example
├── ngrok.yml / ngrok.yml.example
└── README.md
```

---

## 🧼 Clean Up

```bash
docker-compose down -v
```

This stops all containers and removes associated volumes.

---

## 🛠 Notes

- Drupal files are stored in a Docker-managed volume (`drupal_data`)
- Database data is stored in `db_data`
- This stack is designed for local development and testing purposes only

---

##  Legal Notices
This is an example solution subject to the [MIT license](./LICENSE).

## Disclaimer
This document is provided for information purposes only. Paul Taylor may change the contents hereof without notice. This document is not warranted to be error-free, nor subject to any other warranties or conditions, whether expressed orally or implied in law, including implied warranties and conditions of merchantability or fitness for a particular purpose. Paul Taylor specifically disclaims any liability with respect to this document and no contractual obligations are formed either directly or indirectly by this document. The technologies, functionality, services, and processes described herein are subject to change without notice.
