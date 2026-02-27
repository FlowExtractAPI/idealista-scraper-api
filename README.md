# 🏠 Idealista API Scraper

Fast, reliable property scraper for **Idealista.com**, **Idealista.pt**, and **Idealista.it** using the official mobile API. Optimized for speed and accuracy with multi-country support.

---

## 🎯 What This Actor Extracts

Complete property intelligence from Idealista listings:

### 📋 Core Property Data
* **Property Details**: ID, title, description, address, and web link
* **Pricing**: Price amount with currency formatting (€/month or €)
* **Specifications**: Rooms, bathrooms, constructed area, usable area
* **Property Type**: Extended property type (flat, house, villa, etc.)
* **Status**: Active/inactive listing status
* **Listing Updates**: Last modification timestamp

### 🖼️ Visual Content
* **Image Gallery**: High-resolution property photos with captions
* **Thumbnail**: Primary property image
* **Multimedia**: Video content when available
* **Professional Photos**: Idealista-made professional imagery
* **360° Tours**: Virtual tour availability

### 🏢 Location & Contact
* **Address**: Full street address with administrative levels
* **GPS Coordinates**: Latitude and longitude for mapping
* **Location Details**: City, region, district information
* **Contact Name**: Property owner or agent name
* **Phone Number**: Contact phone with country code
* **User Type**: Private owner or professional agent
* **Communication**: Chat and form availability

### 🏗️ Building & Amenities
* **Building Features**: Elevator, parking availability
* **Exterior Access**: Garden, terrace availability
* **Condition**: Good/bad/unknown property status
* **Floor Info**: Floor number and building details
* **Energy Performance**: Energy efficiency when available

### ⚡ Advanced Features
* **Multi-country Support**: Spain (.com), Portugal (.pt), Italy (.it)
* **Auto Language Detection**: Extracts language from URL
* **Auto Country Routing**: Detects correct API endpoint
* **Error Tracking**: Failed items with detailed error messages
* **Pagination Support**: Multi-page property collection
* **Real-time Streaming**: NDJSON format in Standby mode

---

## 🌐 Supported Domains

Extract from any public Idealista property URL:

* `https://www.idealista.com/en/inmueble/82100417/`
* `https://www.idealista.pt/fr/imovel/33939171/`
* `https://www.idealista.it/it/immobile/34613312/`

---

## 📊 Two Operation Modes

### ⚡ **NORMAL Mode** (Batch Processing)
Process one or multiple property URLs in a single actor run:

```json
{
  "Property_urls": [
    { "url": "https://www.idealista.com/en/inmueble/82100417/" },
    { "url": "https://www.idealista.pt/fr/imovel/33939171/" },
    { "url": "https://www.idealista.it/it/immobile/34613312/" }
  ]
}
```

**Output**: Dataset with complete property data for all URLs

---
### **ACTOR STANDBY**

### 🔄 **STANDBY Mode** (Real-Time API)
Keep the actor running as an HTTP server for instant property extraction:

#### **Traditional Run:**
1. ⏳ Start actor (10-30 seconds)
2. 🔍 Extract property (5-15 seconds)
3. 📊 Return results
4. 🛑 Actor stops

#### **Standby Mode:**
1. 🔍 Extract instantly (5-15 seconds)
2. 📊 Return results immediately
3. 🔄 Stay ready for next request

**Response: 3x faster with zero startup overhead!**

#### **Standby Endpoint Example:**
```bash
curl -X POST https://dz-omar--idealista-scraper.apify.actor/ \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_APIFY_TOKEN" \
  -d '{
    "Property_urls": [
      { "url": "https://www.idealista.com/en/inmueble/82100417/" }
    ]
  }'
```

---

## ✅ Input Schema

### **NORMAL Mode Input:**
```json
{
  "Property_urls": [
    { "url": "https://www.idealista.com/en/inmueble/82100417/" }
  ]
}
```

| Field | Type | Description | Required |
|-------|------|-------------|----------|
| **Property_urls** | array | Array of property URLs | ✅ Yes |

### **STANDBY Mode Input:**
Same as NORMAL mode, plus:

```json
{
  "Property_urls": [...]
}
```
---

## 📤 Sample Output

### **Successful Extraction:**
```json
{
  "adid": 82100417,
  "price": 500,
  "priceInfo": {
    "amount": 500,
    "currencySuffix": "€/month"
  },
  "operation": "rent",
  "propertyType": "homes",
  "extendedPropertyType": "flat",
  "ubication": {
    "title": "Calle Everluz, 1",
    "latitude": 37.1827492,
    "longitude": -6.9736586,
    "administrativeAreaLevel2": "Punta Umbria",
    "administrativeAreaLevel1": "Huelva"
  },
  "moreCharacteristics": {
    "roomNumber": 1,
    "bathNumber": 1,
    "constructedArea": 60,
    "usableArea": 55,
    "exterior": true,
    "lift": true,
    "garden": true,
    "status": "good"
  },
  "multimedia": {
    "images": [
      {
        "url": "https://img4.idealista.com/...",
        "tag": "terrace",
        "localizedName": "Terrace"
      }
    ],
    "videos": []
  },
  "contactInfo": {
    "contactName": "juani",
    "userType": "private",
    "phone1": {
      "formattedPhoneWithPrefix": "+34 608 12 39 91"
    },
    "professional": false
  },
  "detailWebLink": "https://www.idealista.com/inmueble/82100417/",
  "country": "es",
  "status": "success",
  "scrapedAt": "2026-02-04T12:30:45.123Z"
}
```

### **Failed Extraction:**
```json
{
  "url": "https://www.idealista.com/en/inmueble/invalid/",
  "propertyId": null,
  "status": "failed",
  "error": "Could not extract property ID from URL",
  "scrapedAt": "2026-02-04T12:30:45.123Z"
}
```

---

## 🔧 How It Works

**Automatic Detection**: Extracts domain from URL, routes to correct API endpoint automatically.

### **URL Parsing**

| Country | URL Pattern | Example |
|---------|------------|---------|
| Spain | `/inmueble/[ID]/` | `/inmueble/82100417/` |
| Portugal | `/imovel/[ID]/` | `/imovel/33939171/` |
| Italy | `/immobile/[ID]/` | `/immobile/34613312/` |

---

## 🔐 Authentication & Proxy


### **Proxy Configuration**

#### **Free Users:**
Automatic Apify residential proxy (no configuration needed)

#### **Paid Users:**
Premium Evomi proxy with custom credentials:

### **Stream Results to File**
```bash
curl -X POST https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_APIFY_TOKEN" \
  -d '{
    "Property_urls": [
      {"url": "https://www.idealista.com/en/inmueble/82100417/"}
    ]
  }' > property_data.ndjson
```

### **Health Check**
```bash
curl -X GET https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN/health \
```

### **Using Token in Query Parameter**
```bash
curl -X POST "https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN"\
  -H "Content-Type: application/json" \
  -d '{
    "Property_urls": [
      {"url": "https://www.idealista.com/en/inmueble/82100417/"}
    ]
  }'
```

---

## 🎯 Perfect For

### **Single Property Analysis:**
* 🧑‍💼 Real estate agents evaluating listings
* 📈 Investors analyzing specific properties
* 🔍 Content creators gathering data
* 🤖 Developers building automation
* 📱 Apps requiring property lookups

### **Bulk Operations:**
* 📊 Market research and trend analysis
* 🏢 Agency monitoring and tracking
* 📈 Investment portfolio management
* 🔄 Automated listing updates

---

## 📈 Performance Metrics

| Metric | Value |
|--------|-------|
| **Typical Response Time** | 5-15 seconds per property |
| **Standby Startup** | 0 seconds (pre-loaded) |
| **API Success Rate** | 99%+ |
| **Retry Coverage** | 3 automatic attempts |
| **Memory Usage** | 128-512 MB configurable |
| **Concurrent Requests** | Full rate limit support |

---

## 🏗️ Architecture Highlights

### **STANDBY Mode Implementation:**
- Express.js HTTP server
- NDJSON streaming responses
- Real-time progress updates
- Graceful error handling
- Automatic batch processing

### **Data Quality:**
- 6 optimized dataset views
- Field validation
- Error tracking
- Status indicators
- Timestamp tracking

---

## 📊 Status Codes

| Status | Meaning | Action |
|--------|---------|--------|
| **success** | Property extracted successfully | Use data |
| **failed** | Extraction failed | Check error message |
| **migrating** | Server is migrating | Retry request |
| **aborting** | Server shutting down | Restart actor |

---

## 💡 Pro Tips

1. **Use Standby for real-time needs** - 3x faster response
2. **Batch requests efficiently** - Multiple URLs in one call
3. **Monitor error view** - Catch issues early
4. **Check network logs** - Debug API issues
5. **Use appropriate proxies** - RESIDENTIAL recommended

---

## 🤝 Support & Resources

## 📞 Support

### Get Help

- 🌐 **Website**: [flowextractapi.com](https://flowextractapi.com)
- 📧 **Email**: [flowextractapi@outlook.com](mailto:flowextractapi@outlook.com)
- 🙋 **Apify Profile**: [dz_omar](https://apify.com/dz_omar?fpr=smcx63)
- 💬 **GitHub Issues**: [FlowExtractAPI](https://github.com/FlowExtractAPI)

### Social Media

- 💼 **LinkedIn**: [flowextract-api](https://www.linkedin.com/in/flowextract-api/)
- 🐦 **Twitter**: [@FlowExtractAPI](https://x.com/@FlowExtractAPI)
- 📱 **Facebook**: [flowextractapi](https://www.facebook.com/flowextractapi)

## 🌟 Related Actors by FlowExtract API

### 🎬 Video & Media
- **[YouTube Transcript Extractor](https://apify.com/dz_omar/youtube-transcript-metadata-extractor?fpr=smcx63)** - Extract transcripts with timestamps
- **[YouTube Scraper Pro](https://apify.com/dz_omar/Youtube-Scraper-Pro?fpr=smcx63)** - Complete channel and playlist extraction
- **[Zoom Scraper](https://apify.com/dz_omar/zoom-scraper?fpr=smcx63)** - Download recordings and transcripts
- **[Loom Scraper](https://apify.com/dz_omar/loom-video-scraper?fpr=smcx63)** - Loom video and transcript extraction

### 🏠 Real Estate
- **[Idealista Scraper API](https://apify.com/dz_omar/idealista-scraper-api?fpr=smcx63)** - Spanish property data with API
- **[Idealista Scraper](https://apify.com/dz_omar/idealista-scraper?fpr=smcx63)** - Real estate listings extractor

### 🛠️ Developer Tools
- **[Screenshot](https://apify.com/dz_omar/screenshot?fpr=smcx63)** - Fast webpage screenshots
- **[Ultimate Screenshot](https://apify.com/dz_omar/ultimate-screenshot?fpr=smcx63)** - Advanced screenshot tool
- **[Network Security Scanner](https://apify.com/dz_omar/network-security-scanner?fpr=smcx63)** - Security vulnerability scanner

### 📱 Social Media
- **[Facebook Ads Scraper Pro](https://apify.com/dz_omar/facebook-ads-scraper-pro?fpr=smcx63)** - Extract Facebook ads data

---

### **⚖️ Legal & Compliance**
- **Public Data Access**: Only processes publicly available Facebook Ad Library data
- **Rate Limiting**: Respects Facebook's service limits and terms of use
- **Data Protection**: No storage of personal information or unauthorized data collection
- **Commercial Use**: Suitable for business intelligence and research applications

---
