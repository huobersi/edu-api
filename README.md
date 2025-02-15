# http-api

## 🌐 URL & Zugriff auf die API
```
http://<ip-adresse>:<port>/api/<endpunkt>
```
🔹 **Erklärung:**
- `<ip-adresse>` → Server-IP
- `:80` → Standard-HTTP-Port
- `/api/<endpunkt>` → API-Endpunkt

### 🔹 Beispiele für den Zugriff:
- **API-Status abrufen:**
  ```
  http://10.30.18.250/api/state
  ```
- **Basic-Auth für `/api/datastore` erforderlich** (Postman, Browser oder cURL nutzbar):
  ```bash
  curl -u <username>:<passwort> http://10.30.18.250/api/datastore
  ```

---
## 🚀 Unterstützte Methoden
```bash
GET, POST, PUT, PATCH, DELETE
OPTIONS => nicht implementiert
HEAD => nicht implementiert
```

---
## 📌 API-Endpunkte
### 🟢 API-Status - Request
| **Methode**  | **Endpoint**  | **Beschreibung** |
|-------------|-------------|------------------|
| **GET**     | `/api/state` | API-Status abrufen |

#### 🔄 API-Status - Response
```json
{
    "state": "Online",
    "name": "Huober-API",
    "datum": "2025-02-15T16:59:05.461Z",
    "statuscode": 200,
    "message": "Erfolgreicher GET - Request"
}
```

---
### 🟢 Userdaten - Request
| **Methode**  | **Endpoint**                | **Beschreibung** |
|-------------|----------------------------|------------------|
| **GET**     | `/api/userdata/`           | Alle Benutzerdaten abrufen |
| **GET**     | `/api/userdata/at_userX/`  | Daten für spezifischen Nutzer abrufen |

---
### 📂 Ungeschützter JSON-Datenspeicher - Request
| **Methode**  | **Endpoint**      | **Beschreibung** |
|-------------|-----------------|------------------|
| **GET**     | `/api/speicher`  | JSON-Daten abrufen |
| **POST**    | `/api/speicher`  | JSON-Daten hinzufügen |
| **PUT**     | `/api/speicher`  | JSON-Daten überschreiben |
| **PATCH**   | `/api/speicher`  | JSON-Daten aktualisieren |
| **DELETE**  | `/api/speicher`  | JSON-Daten löschen |

📌 **Body (JSON-Format):**
```json
{
    "example": "example"
}
```

---
### 🔐 Basic-Auth geschützter JSON-Datenspeicher - Request
| **Methode**  | **Endpoint**       | **Beschreibung**              | **Username** | **Passwort** |
|-------------|------------------|------------------------------|-------------|-------------|
| **GET**     | `/api/datastore`  | Datenspeicher abrufen        | erforderlich | erforderlich |
| **POST**    | `/api/datastore`  | Datenspeicher hinzufügen     | erforderlich | erforderlich |
| **PUT**     | `/api/datastore`  | Datenspeicher überschreiben  | erforderlich | erforderlich |
| **PATCH**   | `/api/datastore`  | Datenspeicher aktualisieren  | erforderlich | erforderlich |
| **DELETE**  | `/api/datastore`  | Datenspeicher löschen        | erforderlich | erforderlich |

📌 **Body (JSON-Format):**
```json
{
    "example": "example"
}
```

📌 **Basic Authentication in Postman:**
1. **Authorization > Auth Type > Basic Auth**
2. **Benutzername & Passwort eingeben**
