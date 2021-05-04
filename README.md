# Prueba técnica Frontend Developer (vue)

## ¿Qué se busca evaluar?
* Creatividad para resolver los requerimientos
* Calidad del código entregado (estructura y buenas prácticas)
* Eficiencia de los algoritmos entregados
* Familiaridad con el stack de desarrollo y método de autentificación de APIs

## Objetivo

Crear una app web que contenga un CRUD de dispositivos, haciendo uso de la API REST de The Group Cloud.

## Requerimientos

* CRUD de dispositivos
* Utilizar Vue como framework frontend
* No tardar más de 8 horas en realizar el ejercicio (no importa si queda incompleto)
* No es necesario incluir un login (las credenciales pueden estar en el código)
* No es necesario incluir un paginador, es suficiente con que se muestre la primera página

## Deseable

* Vuex
* Vue Router
* Vuetify

## Fuente de datos

#### POST /login

##### Request body:
```javascript
{
    "email": "test@user.com",
    "password": "password"
}
```

##### Response:
```javascript
{
    "user": {
        "id": 1,
        "name": "Test User",
        "email": "test@user.com",
        "organization_id": 1,
        "email_verified_at": null,
        "created_at": "2021-04-27T13:19:22.000000Z",
        "updated_at": "2021-04-27T13:19:22.000000Z",
        "tz": "America/Santiago",
        "needs_to_change_password": false
    },
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9...."
}
```

#### GET /devices

##### Response:
```javascript
{
    "current_page": 1,
    "data": [
        {
            "id": 3,
            "identifier": "35963210222224",
            "alias": "Credential 3",
            "device_type": "Credential",
            "technology_type": "GSM Bands",
            "worker_name": "Worker",
            "worker_last_name": "Test",
            "timestamp": "2021-04-27 09:19:23"
        },
        {
            "id": 2,
            "identifier": "3596321111115642",
            "alias": "Credential 2",
            "device_type": "Credential",
            "technology_type": "GSM Bands",
            "worker_name": "Worker2",
            "worker_last_name": "Test",
            "timestamp": "2021-04-27 09:19:23"
        }
    ],
    "first_page_url": "http://localhost:8000/api/devices?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "http://localhost:8000/api/devices?page=1",
    "next_page_url": null,
    "path": "http://localhost:8000/api/devices",
    "per_page": 15,
    "prev_page_url": null,
    "to": 3,
    "total": 3
}
```

#### GET /device/{device_id}

```json
{
    "id": 1,
    "identifier": "359632222625871",
    "mac": "E1A12222E380",
    "device_type_id": 5,
    "technology_type_id": 5,
    "organization_id": 1,
    "worker_id": 1,
    "alias": "Credential 1",
    "scope": 0,
    "has_gps": false,
    "active": true,
    "icon_id": 1,
    "created_at": "2021-04-27T13:19:23.000000Z",
    "updated_at": "2021-04-27T13:19:23.000000Z"
}
```

#### POST /device

##### Body request:
```javascript
{
    "identifier": "DeviceIdentifier123", //required
    "mac": "DeviceMAC123",
    "device_type_id": 1, //required
    "technology_type_id": 1, //required
    "alias": "Device123", //required
    "scope": 0,
    "has_gps": false
}
```
##### Response:
```javascript
{
    "identifier": "DeviceIdentifier123",
    "mac": "DeviceMAC123",
    "device_type_id": 1,
    "worker_id": null,
    "scope": 0,
    "has_gps": false,
    "technology_type_id": 1,
    "organization_id": 1,
    "alias": "Device123",
    "updated_at": "2021-05-04T12:16:39.000000Z",
    "created_at": "2021-05-04T12:16:39.000000Z",
    "id": 9
}
```

#### PUT /device

##### Body request:
```javascript
{
    "id": 9, //required
    "identifier": "DeviceIdentifier1234", //required
    "mac": "DeviceMAC1234",
    "device_type_id": 2, //required
    "technology_type_id": 2, //required
    "alias": "Device1234", //required
    "scope": 0,
    "has_gps": false
}
```
##### Response:
```javascript
{
    "id": 9,
    "identifier": "DeviceIdentifier1234",
    "mac": "DeviceMAC1234",
    "device_type_id": 2,
    "technology_type_id": 2,
    "organization_id": 1,
    "worker_id": null,
    "alias": "Device1234",
    "scope": 0,
    "has_gps": false,
    "active": true,
    "icon_id": 1,
    "created_at": "2021-05-04T12:16:39.000000Z",
    "updated_at": "2021-05-04T12:23:57.000000Z"
}
```

#### DELETE /device/{device_id}

##### Response:
```javascript
{
    "message": "The device was deleted successfully"
}
```

#### GET /technology-types

##### Response:
```javascript
[
    {
        "id": 1,
        "name": "WiFi"
    },
    {
        "id": 2,
        "name": "Ethernet"
    },
    {
        "id": 3,
        "name": "LoRa"
    },
    {
        "id": 4,
        "name": "LoRaWan"
    },
    {
        "id": 5,
        "name": "GSM Bands"
    },
    {
        "id": 6,
        "name": "XBee"
    }
]
```

#### GET /device-types

##### Response:
```javascript
[
    {
        "id": 1,
        "name": "Gateway"
    },
    {
        "id": 2,
        "name": "Transmitter"
    },
    {
        "id": 3,
        "name": "Receiver"
    },
    {
        "id": 4,
        "name": "Transmitter and receiver"
    },
    {
        "id": 5,
        "name": "Credential"
    }
]
```
## Cómo entregar
* Clonar este repositorio en su máquina local
* Crear una nueva rama utilizando su nombre completo
* Crear una pull request de esa rama

Las credenciales serán entregadas junto con la prueba técnica.
