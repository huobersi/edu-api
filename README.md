## 🔧Query-String – URL-Parameter
| **Methode** | **Endpoint** | **Parameter** | **Beschreibung** |
|------------|-------------|--------------|------------------|
| **GET** | `http://edu-api.huoberiot.com/api/users.json` | Keine oder `?at_enableX=on` | Ruft alle Benutzer oder nur aktivierte Benutzer ab. |
| **POST** | `http://edu-api.huoberiot.com/api/users.json` | JSON-Daten | Erstellt einen neuen Benutzer. |
| **PUT** | `http://edu-api.huoberiot.com/api/users.json` | JSON-Daten | Aktualisiert einen vorhandenen Benutzer. |
| **DELETE** | `http://edu-api.huoberiot.com/api/users.json` | `?at_usernameX=admin` | Löscht einen Benutzer mit einem bestimmten Benutzernamen. |


# 📌 Inbetriebnahme & Nutzung der HTTP-API 
## 🔧 Anfragen - Internet - Online (ohne Installation)
**Web-Interface aufrufen - http und https möglich!!**
   - **🔗 http://edu-api.huoberiot.com:80** (API-Nutzung)
   - **🔗 https://edu-api.huoberiot.com:443** (API-Nutzung)
   - **🔗 https://edu-api.huoberiot.com/ui** (Dashboard)
   - **🔗 https://edu-api.huoberiot.com/admin** (Admin-Seite, Login erforderlich)

**📌 Hinweis: Für Debugging mit Wireshark sollte HTTP verwendet werden.**

## 🔧 Installation & Einrichtung - Offline - (lokaler Node-RED Betrieb via .bat)
### 1. Node-RED API-Vorlage vorbereiten
1. **ZIP-Datei entpacken**
   - 📁 **`250215_API_HTTP-Node-RED_LuL_Master.zip`** entpacken.
2. **Ordner verschieben**
   - Verschiebe **`250215_API_HTTP-Node-RED_LuL_Master`** nach **`C:\`**.
3. **Node-RED starten**
   - **`node-red.bat`** ausführen.
4. **Web-Interface aufrufen - http und https möglich!!**
   - **🔗 http://<ip/url-adresse>:80** (API-Nutzung)
   - **🔗 https://<ip/url-adresse>/ui** (Dashboard)
   - **🔗 https://<ip/url-adresse>/admin** (Admin-Seite, Login erforderlich)

## 📂 Bereitgestellte Dateien
| Datei | Beschreibung |
|----------------|--------------------------------|
| `250215_API_HTTP-Node-RED_LuL_Master.zip` | Komplettes ZIP-Archiv mit API-Vorlagen |
| `250215_API_HTTP_Node-RED_Vorlage_flows.json` | Node-RED Flow-Vorlage für die API |
| `api` | c:\250215_API_HTTP-Node-RED_LuL_Master\node-v20.15.1\api\ |
| `iot-node-red-settings.js` | Einstellungen Port / Dateipfade |

# 🌐 URL & Zugriff auf die API
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
  http://<ip/url-adresse>/api/state
  https://<ip/url-adresse>/api/state
  ```
- **Basic-Auth für `/api/endpoint` erforderlich** (Postman, Browser oder cURL nutzbar):
  ```bash
  curl -u <username>:<passwort> http://<ip/url-adresse>/api/endpoint
  ```

![Postman - Zugriff](:/9daf3dec55684762947d7b8ba37b1e6a)

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
### 🟢 /ui - Platznummer - Request - Post
| **Methode**  | **Endpoint**                | **Body - RAW** |
|-------------|----------------------------|------------------|
| **POST**     | `/api/platz/<zahl><buchstabe>` | True oder False |

📌 **Body (RAW-Format):**
```raw
True 
```
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

### 🔐 API-KEY Auth geschützter JSON-Datenspeicher - Request
| **Methode**  | **Endpoint**       | **Beschreibung**              | **API-Key** | **Header** |
|-------------|------------------|------------------------------|-------------|-------------|
| **GET**     | `/api/example`  | Datenspeicher abrufen        | erforderlich | erforderlich |
| **POST**    | `/api/example`  | Datenspeicher hinzufügen     | erforderlich | erforderlich |
| **PUT**     | `/api/example`  | Datenspeicher überschreiben  | erforderlich | erforderlich |
| **PATCH**   | `/api/example`  | Datenspeicher aktualisieren  | erforderlich | erforderlich |
| **DELETE**  | `/api/example`  | Datenspeicher löschen        | erforderlich | erforderlich |

📌 **Body (JSON-Format):**
```json
{
    "example": "example"
}
```

📌 **Basic Authentication in Postman:**
1. **Authorization > Auth Type > Basic Auth**
2. **Benutzername & Passwort eingeben**

