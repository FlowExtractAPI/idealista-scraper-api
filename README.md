# 🏠 Idealista API Scraper

Fast, reliable property scraper for **Idealista.com** (Spain), **Idealista.pt** (Portugal), **Idealista.it** (Italy) and **Idealista.fr** (France). Optimized for speed and accuracy with multi-country support.

**Supports every Idealista search URL type  single property, listing/search, multi-area, hand-drawn map regions, and map-pin point searches.**

- A short guide on how to use **[ Idealista API Scraper](https://apify.com/dz_omar/idealista-scraper-api?fpr=smcx63)** Actors :

https://www.youtube.com/watch?v=fuxnnvB5538

---

## 🚀 What's New  Scrape Virtually the Entire Site

This release is a major step up from previous versions. **You can now collect practically every listing for a search area, no matter how large  even regions with tens of thousands of properties.**

Large areas used to hit a hard ceiling: a single Idealista search only ever serves a limited slice of its results, so big regions came back capped and padded with repeats. This version removes that ceiling. Ask for a high `desiredResults` on a large area and the actor delivers a deep, **de-duplicated** result set that reaches far beyond what one search can return  every row is a distinct property.

It also now handles **every kind of Idealista search URL**, exactly as the website produces it:

* 🗺️ **Draw an area on the map**  paste a hand-drawn map-region URL and get every property inside that exact shape.
* 📍 **Drop a pin on a location**  paste a map-pin (`/point/...`) URL and get the properties around that spot, with your filters applied.
* 🧩 **Select multiple zones**  paste a multi-area URL and get every property across all the zones you picked, in one run.
* 🔗 **Any Idealista URL**  single property, listing/search, filtered (price, size, type), in any supported language  just copy from your browser and paste it in.

Whatever URL Idealista gives you  however the area is defined  the actor processes it correctly. Filters in the URL (price, size, property subtype, etc.) are fully respected throughout.

> No special setup is required: paste your URL, set how many results you want, and run.

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
* **Galleries on All URL Types**: Full image galleries now returned for listing, search, and map-area URLs  not just single property pages
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
* **Multi-country Support**: Spain (.com), Portugal (.pt), Italy (.it), France (.fr)
* **Map-Area Search**: Scrape any custom region drawn on Idealista's map
* **Multi-Area Search**: Scrape several selected zones/neighbourhoods in one run
* **Point / Map-Pin Search**: Scrape the area around a map-pin location URL
* **Agency Pages**: Scrape every listing of an agency from its Idealista page
* **Auto Language Detection**: Results follow the language of your URL
* **Auto Country Detection**: Paste URLs from any supported country — no setting needed
* **Mixed URL Support**: Property URLs and listing/search URLs in one request
* **Filters Respected**: Price, size, type and every other filter in your URL is applied
* **Configurable Results**: Control max properties per listing URL
* **Error Tracking**: Failed items with detailed error messages
* **Pagination Support**: Multi-page property collection
* **Real-time Streaming**: NDJSON format in Standby mode

---

## 🌐 Supported URL Types

### Individual Property URLs
Extract data from a single property page:

* `https://www.idealista.com/en/inmueble/82100417/`
* `https://www.idealista.pt/fr/imovel/33939171/`
* `https://www.idealista.it/it/immobile/34613312/`
* `https://www.idealista.fr/en/immeuble/174279/`

### Listing/Search URLs
Scrape multiple properties from a search results page:

* `https://www.idealista.com/en/venta-viviendas/balears-illes/?ordenado-por=precios-asc`
* `https://www.idealista.pt/fr/comprar-casas/nordeste/achadinha/`
* `https://www.idealista.it/pt/vendita-case/alice-castello-vercelli/`
* `https://www.idealista.fr/en/achat-logement/paris-paris-75/`

### Agency URLs
Scrape the listings of one agency, with or without a location:

* `https://www.idealista.fr/en/pro/liberkeys/achat-logement/`

The actor automatically detects which type of URL you provide and handles each accordingly.

---

### Map-Area / Drawn-Region URLs (NEW)
Scrape every property inside a custom area you draw on Idealista's map:

* `https://www.idealista.it/it/aree/vendita-case/.../lista-mappa?shape=...`
* `https://www.idealista.fr/en/aires/location-local/.../carte-google?shape=...`

Draw any region on Idealista's map search, copy the URL, and paste it in  the actor scrapes all matching properties within that exact area. Works across Spain, Portugal, Italy and France.

---

### Multi-Area URLs (NEW)
Scrape across several neighbourhoods or zones selected together in one search:

* `https://www.idealista.com/en/multi/alquiler-viviendas/.../`
* `https://www.idealista.pt/es/multi/comprar-casas/.../`
* `https://www.idealista.it/multi/vendita-case/.../`
* `https://www.idealista.fr/en/multi/location-bureaux/akL,bXZ/`

Select multiple zones on Idealista, copy the URL, and paste it in  the actor scrapes properties from all selected zones in a single run.

---

### Point / Map-Pin URLs (NEW)
Scrape properties around a specific point on the map (the `/point/...` URLs Idealista creates when you search around a location):

* `https://www.idealista.com/en/point/venta-viviendas/.../mapa-google`
* `https://www.idealista.pt/es/point/comprar-casas/.../mapa-google`
* `https://www.idealista.it/en/point/vendita-uffici/.../lista-mappa`

Search around a spot on Idealista's map, copy the URL, and paste it in  the actor scrapes the properties in that area, with all your filters applied.

> **Note on point URLs:** a map-pin search returns the properties in the surrounding map area. For an exact, precisely-bounded selection, use a hand-drawn **Map-Area** URL (above), which captures the precise region you select.

## 📊 Two Operation Modes

### ⚡ **NORMAL Mode** (Batch Processing)
Process property URLs and listing URLs in a single actor run:

```json
{
  "Property_urls": [
    { "url": "https://www.idealista.com/en/venta-viviendas/balears-illes/?ordenado-por=precios-asc" },
    { "url": "https://www.idealista.com/en/inmueble/82100417/" },
    { "url": "https://www.idealista.pt/fr/imovel/33939171/" },
    { "url": "https://www.idealista.it/it/immobile/34613312/" }
  ],
  "desiredResults": 10
}
```

In this example, the actor returns:
- Up to **10 properties** from the listing URL (`/venta-viviendas/balears-illes/`)
- **1 property each** from the 3 individual property URLs
- **Total**: up to 13 properties

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
curl -X POST https://dz-omar--idealista-scraper-api.apify.actor/ \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_APIFY_TOKEN" \
  -d '{
    "Property_urls": [
      { "url": "https://www.idealista.com/en/venta-viviendas/balears-illes/" },
      { "url": "https://www.idealista.com/en/inmueble/82100417/" }
    ],
    "desiredResults": 10
  }'
```

---

## ✅ Input Schema

### **Input Fields:**

| Field | Type | Required | Default | Description |
|-------|------|----------|---------|-------------|
| **Property_urls** | array | ✅ Yes |  | Array of property or listing URLs |
| **detailMode** | boolean | No | false | 🔎 **Fetch full property details.** When ON, every property from a listing/search URL is returned as a full detail record (all images, complete multilingual descriptions, agent contacts, energy certification) — slower and richer, billed at the detailed rate. When OFF (default), listing/search results come with the data available in search results — faster, billed at the standard rate. Individual property URLs always return the full detail record and are billed at the detailed rate, whatever this setting. |
| **desiredResults** | integer | No | 10 | Max properties per listing URL. Set it high (thousands) on a large area to collect deep, de-duplicated coverage; set it low for a quick sample. |

### **Example Input (Mixed URLs):**
```json
{
  "Property_urls": [
    { "url": "https://www.idealista.com/en/venta-viviendas/balears-illes/?ordenado-por=precios-asc" },
    { "url": "https://www.idealista.com/en/inmueble/82100417/" },
    { "url": "https://www.idealista.pt/fr/imovel/33939171/" },
    { "url": "https://www.idealista.it/it/immobile/34613312/" }
  ],
  "desiredResults": 11
}
```

**How it works:**
- The listing URL (`/venta-viviendas/...`) returns up to `desiredResults` (11) properties
- Each property URL (`/inmueble/`, `/imovel/`, `/immobile/`) returns exactly 1 property
- **Total output**: up to 14 properties (11 + 3)

### **💰 How results are billed**

You pay per result, and the rate follows the record you receive (see the Pricing tab for amounts):

| What you get | Rate |
|---|---|
| A property from a listing/search URL, **Fetch full property details OFF** | Standard |
| A property from a listing/search URL, **Fetch full property details ON** | Detailed |
| An **individual property URL** (always the full detail record) | Detailed |
| A listing result whose full details could not be retrieved (returned with search-result data) | Standard |
| A removed listing, an unknown property ID, or a URL that could not be searched | Not billed |

### **STANDBY Mode Input:**
Same format, sent as POST body to the standby endpoint.

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

## ❓ Why did my run return no properties?

Every run ends with a short **status message** (shown at the top of the run in the Console) that says how many results were saved and whether anything needs your attention.

* **"N search(es) matched no properties right now"**  the search worked, Idealista simply has no listings matching it at the moment (common with filters such as *published in the last 24 hours*). Nothing is wrong  try wider filters or run it again later.
* **"N URL(s) could not be searched as given"**  the dataset contains a row with `"status": "failed"` and an `error` field explaining how to fix that URL. These rows are not billed.
* **"Some requests to Idealista failed after several retries"**  a temporary connection problem; run it again.

**The easiest way to get a working URL:** run your search on Idealista (location, filters, map area), then copy the URL straight from the browser's address bar. If you build URLs yourself, the filter part of the URL must start with Idealista's filter prefix:

| Site | Filter prefix | Example |
|------|---------------|---------|
| idealista.com (Spain) | `con-` | `/alquiler-viviendas/madrid-madrid/con-precio-hasta_1500/` |
| idealista.it (Italy) | `con-` | `/vendita-case/roma-roma/con-prezzo_300000/` |
| idealista.pt (Portugal) | `com-` | `/comprar-casas/lisboa/com-preco-max_300000/` |
| idealista.fr (France) | `avec-` | `/location-bureaux/dordogne-24/avec-surface-m2-min_40/` |

---

## 🔐 Authentication & Proxy

### **Proxy Configuration**

No proxy setup is required — it's fully automatic.

#### **Free Users:**
Automatic Apify residential proxy (no configuration needed).

#### **Paid Users:**
A premium proxy with **automatic failover** to the standard proxy — if the premium
route has a hiccup, the run switches over seamlessly and keeps going, so a proxy
issue never interrupts your results.

### **Stream Results to File**
```bash
curl -X POST "https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "Property_urls": [
      {"url": "https://www.idealista.com/en/venta-viviendas/balears-illes/"},
      {"url": "https://www.idealista.com/en/inmueble/82100417/"}
    ],
    "desiredResults": 20
  }' > property_data.ndjson
```

### **Health Check**
```bash
curl -X GET "https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN/health"
```

### **Using Token in Query Parameter**
```bash
curl -X POST "https://dz-omar--idealista-scraper-api.apify.actor?token=YOUR_APIFY_TOKEN" \
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
* 🗺️ Regional property scanning via listing URLs

---

## 📈 Performance Metrics

| Metric | Value |
|--------|-------|
| **Typical Response Time** | 5-15 seconds per property |
| **Standby Startup** | 0 seconds (pre-loaded) |
| **API Success Rate** | 99%+ |
| **Retry Coverage** | Automatic retries on temporary errors |
| **Memory Usage** | 128-512 MB configurable |
| **Concurrent Requests** | Full rate limit support |

---

## 🏗️ Highlights

### **STANDBY Mode:**
- Always-on HTTP endpoint
- NDJSON streaming responses
- Mixed URL handling (property + listing)
- Real-time progress updates
- Graceful error handling
- Automatic batch processing

### **Listing URLs:**
- Paste the URL exactly as Idealista shows it
- Automatic pagination with configurable limits
- Batch streaming in STANDBY mode

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
| **deactivated** | The listing was removed from Idealista; its last known details are included | Use or skip |
| **not_found** | No listing exists with this ID | Check the URL |
| **failed** | Extraction failed | Check error message |
| **migrating** | Server is migrating | Retry request |
| **aborting** | Server shutting down | Restart actor |

---

## 💡 Pro Tips

1. **Use Standby for real-time needs** - 3x faster response
2. **Mix URL types** - Combine property and listing URLs in one request
3. **Set desiredResults wisely** - Higher values = more data but longer runtime
4. **Batch requests efficiently** - Multiple URLs in one call
5. **Monitor error view** - Catch issues early

---

## 🌟 Related Actors by FlowExtract API

### 🎬 Video & Media
- **[YouTube Transcript Extractor](https://apify.com/dz_omar/youtube-transcript-metadata-extractor?fpr=smcx63)** - Extract transcripts with timestamps
- **[YouTube Scraper Pro](https://apify.com/dz_omar/Youtube-Scraper-Pro?fpr=smcx63)** - Complete channel and playlist extraction
- **[Zoom Scraper](https://apify.com/dz_omar/zoom-scraper?fpr=smcx63)** - Download recordings and transcripts
- **[Loom Scraper](https://apify.com/dz_omar/loom-video-scraper?fpr=smcx63)** - Loom video and transcript extraction

### 🏠 Real Estate
- **[Idealista Scraper API](https://apify.com/dz_omar/idealista-scraper-api?fpr=smcx63)** - Spanish property data with API
- **[Idealista Scraper](https://apify.com/dz_omar/idealista-scraper?fpr=smcx63)** - Real estate listings extractor

### 📚 Education & Community
- **[Skool Scraper Pro](https://apify.com/dz_omar/skool-scraper-pro?fpr=smcx63)**  Lessons, videos, posts, and attachments from Skool classrooms
- **[Skool Map Scraper](https://apify.com/dz_omar/skool-map-scraper?fpr=smcx63)**  Member locations and profiles from Skool community maps

### 🛠️ Developer Tools
- **[Screenshot](https://apify.com/dz_omar/screenshot?fpr=smcx63)** - Fast webpage screenshots
- **[Ultimate Screenshot](https://apify.com/dz_omar/ultimate-screenshot?fpr=smcx63)** - Advanced screenshot tool
- **[Network Security Scanner](https://apify.com/dz_omar/network-security-scanner?fpr=smcx63)** - Security vulnerability scanner

### 📱 Social Media
- **[Facebook Ads Scraper Pro](https://apify.com/dz_omar/facebook-ads-scraper-pro?fpr=smcx63)** - Extract Facebook ads data

---

## Support

- 🌐 **Website:** [flowextractapi.com](https://flowextractapi.com)
- 📧 **Email:** [flowextractapi@outlook.com](mailto:flowextractapi@outlook.com)
- 💬 **GitHub:** [FlowExtractAPI](https://github.com/FlowExtractAPI)
- 💼 **LinkedIn:** [flowextract-api](https://www.linkedin.com/in/flowextract-api/)
- 🐦 **X (Twitter):** [@FlowExtractAPI](https://x.com/FlowExtractAPI)
- 📱 **Facebook:** [flowextractapi](https://www.facebook.com/flowextractapi)
- 🎵 **TikTok:** [@flowextractapi](https://www.tiktok.com/@flowextractapi)

## Legal & compliance

- **Public data only** — processes publicly available data.
- **Rate limiting** — respects source-service limits and terms of use.
- **Data protection** — no storage of personal information or unauthorized data collection.
- **Commercial use** — suitable for business intelligence and research.
- No affiliation with or endorsement by Idealista is implied.

---

*Idealista Scraper API — by FlowExtract API. Turn any website into structured data.*