# WebServices

**3 key featues for web serivices**.

* designed for machine-to-machine interaction (application to application)
* platform independent (interoperable)
* communication over network

**Service Definition**

1. Request/Response Formate
2. Request Structure
3. Response Stucture
4. End Point

Message exchange formate ( xml, json etc)

Transport ( HTTP, MQ etc)

Service Provider (Server)

Service Consumer (Client)

SOAP-based (Simple Object Access Protocol)

```
SOAP-ENV:Envelop
SOAP-ENV:Header
SOAP-ENV:Body
```

```
Format
    SOAP XML request
    SOAP XML response
Transport
    SOAP over MQ
    SOAP over HTTP
Service Definition
    WSDL (Web service definition language)
        WSDL defines
            1. Endpoint
            2. All Operations
            3. Request Structure
            4. Response Structure
```

REST (REpresentational State Transfer)

| REST                              |                              |
| --------------------------------- | ---------------------------- |
| HTTP                              |                              |
| HTTP Methods (GET, POST, PUT etc) | HTTP Response (200, 400 etc) |

```
    REST
Data Exchnage Format
    No restrition, Json is popular
Transport
    Only HTTP
Service Defintion
    No Standard, WADL(Web Application Defintion Language) /Swagger etc 
```

