# FTP.BD API

**A public API for accessing FTP servers and media server information in Bangladesh.**

[![API Status](https://img.shields.io/badge/API-Public-brightgreen)](https://ftp.bd/api/api.php)
[![Format](https://img.shields.io/badge/Response-JSON-blue)](https://ftp.bd/api/api.php)
[![Website](https://img.shields.io/badge/Website-ftp.bd-orange)](https://ftp.bd)

## Overview

The FTP.BD API provides structured information about FTP servers, media servers, and other ISP-based online services in Bangladesh.

Developers can integrate this API into websites, applications, dashboards, and other projects to retrieve server information in JSON format.

## API Endpoint

**Base URL:**

```text
https://ftp.bd/api/api.php
```

**Request Method:** `GET`

**Response Format:** `JSON`

**Authentication:** Not required for the publicly accessible endpoint.

## API Response

The API returns a JSON object containing the total number of servers and an array of server information.

### Example Response

```json
{
  "total": 79,
  "servers": [
    {
      "id": "60d8f0a3-ba6e-4094-8310-1c155bb4fd53",
      "name": "FlickFox",
      "isp": "All ISP supported",
      "url": "https://flickfox.pw/",
      "region": "",
      "status": "online",
      "speed": "0",
      "ping": "3",
      "tags": [
        "Movies"
      ]
    }
  ]
}
```

*Note: The example is shortened for demonstration purposes. Actual responses may contain multiple server entries.*

## Response Parameters

| Parameter | Type | Description |
|---|---|---|
| `total` | Integer | Total number of servers returned |
| `servers` | Array | Collection of server information |
| `id` | String | Unique server identifier |
| `name` | String | Server name |
| `isp` | String | Internet service provider |
| `url` | String | Server website or access URL |
| `region` | String | Server region |
| `status` | String | Current reported status |
| `speed` | String | Reported server speed |
| `ping` | String | Reported ping value |
| `tags` | Array | Server categories or supported content types |

Some fields may contain empty values depending on the available server information.

## Usage Examples

### 1. cURL

Retrieve server information using cURL:

```bash
curl -X GET "https://ftp.bd/api/api.php" \
     -H "Accept: application/json"
```

### 2. JavaScript (Fetch API)

```javascript
fetch("https://ftp.bd/api/api.php")
  .then(response => {
    if (!response.ok) {
      throw new Error("API request failed");
    }
    return response.json();
  })
  .then(data => {
    console.log("Total Servers:", data.total);
    console.log("Servers:", data.servers);
  })
  .catch(error => {
    console.error("Error:", error);
  });
```

### 3. PHP

```php
<?php

$apiUrl = "https://ftp.bd/api/api.php";

$response = file_get_contents($apiUrl);

if ($response !== false) {
    $data = json_decode($response, true);

    if (json_last_error() === JSON_ERROR_NONE) {
        echo "Total Servers: " . $data['total'];

        foreach ($data['servers'] as $server) {
            echo "<h3>" . htmlspecialchars($server['name']) . "</h3>";
            echo "<p>ISP: " . htmlspecialchars($server['isp']) . "</p>";
            echo "<p>Status: " . htmlspecialchars($server['status']) . "</p>";
            echo "<a href='" . htmlspecialchars($server['url']) . "'>Visit Server</a>";
        }
    }
}
?>
```

## Available Server Categories

Servers may include different categories through the `tags` parameter, such as:

- Movies
- General
- TV
- Anime
- Video
- Games
- Software

The available categories depend on the server information maintained by FTP.BD.

## Important Notes

- The API is publicly accessible.
- Server information may change over time.
- Availability and ping values are subject to change.
- Some servers may only be accessible through specific ISP networks.
- An `online` status does not guarantee accessibility from every network.
- Empty fields indicate that information is currently unavailable.
- Please handle API errors and unexpected response values in your application.

## Use Cases

The FTP.BD API can be used to build:

- FTP server directories and listing websites.
- ISP-based media server directories.
- Server status dashboards.
- Server discovery applications.
- Network and connectivity information tools.

## Disclaimer

FTP.BD provides server information for discovery and informational purposes. Server ownership, availability, content, and access policies are determined by their respective operators.

Users and developers are responsible for complying with applicable laws, copyright regulations, and the terms of service of individual servers.

## Links

- **Official Website:** https://ftp.bd
- **API Endpoint:** https://ftp.bd/api/api.php

---

**Developed and maintained by FTP.BD**

*Discover Bangladesh's FTP and media server ecosystem.*
