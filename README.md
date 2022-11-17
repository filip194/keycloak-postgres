# Keycloak using Postgres as User Federation

---

Keycloak working with Postgres DB docker-compose file

## Setup local volume for postgres data

---

In docker-compose directory of your project, create new directory:
> postgres_data

It will be your local storage for database data and it is ignored by git in this project.

## Running docker-compose file

---

From docker-compose directory run:

docker-compose -f keycloak-server.yml up

## Keycloak realm export/import with users

---

### Keycloak v16 or lower:

Export/Import REALM and USERS:

- https://keepgrowing.in/tools/keycloak-in-docker-5-how-to-export-a-realm-with-users-and-secrets/
- https://keepgrowing.in/tools/keycloak-in-docker-6-how-to-import-realms-from-a-directory/

### Keycloak v17 OR HIGHER:

- https://www.keycloak.org/server/importExport

Connect to docker container:
> docker exec -it keycloak-authorization-server bin/sh

- Export REALM and USERS:

> /opt/keycloak/bin/kc.sh export --dir /tmp/export --realm microservices-realm --users different_files --users-per-file
> 10

- Import REALM and USERS:

> /opt/keycloak/bin/kc.sh import --dir /tmp/export --override true
