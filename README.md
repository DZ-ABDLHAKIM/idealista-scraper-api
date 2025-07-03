# 🏘️ Idealista Property Scraper API

Extract comprehensive real estate data from **single Idealista property listings** across **Spain**, **Portugal**, and **Italy** with unparalleled detail and accuracy.

Perfect for real estate analysts, content creators, investors, and SEO professionals who need structured property data without coding complexity.

---

## 🔎 What This Actor Extracts

This scraper provides **complete property intelligence** from individual listings:

### 📋 Core Property Data
* 📌 **Property Details**: ID, title, description, location, and listing URL
* 💰 **Pricing**: Current listing price with currency formatting
* 📏 **Specifications**: Built area, rooms, bathrooms via propertySpecs
* 🏢 **Property Features**: Detailed characteristics array with all property attributes
* ⚡ **Energy Performance**: Energy efficiency ratings and labels when available
* 📅 **Listing Status**: Last update information (e.g., "updated 17 days ago")

### 🖼️ Visual Content
* 📸 **Image Gallery**: High-resolution photos with titles, descriptions, and tags
* 🖼️ **Main Image**: Primary property photo URL
* 🗺️ **Map Integration**: Google Maps static images with GPS coordinates
* 🎥 **Virtual Tours**: 360° tour URLs when available
* 📋 **Floor Plans**: Architectural layouts marked with isPlan flag

### 🏢 Agency & Contact Information
* 🏛️ **Agency Details**: Professional name, location, logo, and website
* 📞 **Contact Methods**: Phone numbers, chat/form availability flags
* 🔗 **Reference**: Property reference number and agency type
* 📍 **Map Location**: Agency location data when available

### 🏗️ Building & Amenities
* 🏠 **Building Features**: Elevator, parking, construction details
* 🌿 **Amenities**: Swimming pool, garden, terrace, air conditioning
* 🎯 **Property Specs**: Structured data for rooms, bathrooms, area, and boolean amenities

---

## ⚙️ One URL Per Run

This actor is built for **one listing per run**. Want to extract 10 listings? Just call the actor 10 times — either manually or automatically.

> ⚠️ **Perfect for automation**: developers can loop through multiple URLs and call this actor via API.

---

## 🔗 Need Bulk Extraction?

**Looking to scrape hundreds or thousands of properties at once?** 

Check out our **[Idealista Bulk Property Scraper](https://apify.com/dz_omar/idealista-scraper)** which:
- 🚀 **Processes multiple search URLs** in a single run
- 📈 **Extracts unlimited properties** (bypasses Idealista's 1,800-property limit)
- 🤖 **Uses this API internally** for individual property extraction
- 💰 **More cost-effective** for large-scale operations

---

## 🌐 Supported Domains

You can use this actor on any **public Idealista property URL** such as:

* `https://www.idealista.pt/en/imovel/33826216/`
* `https://www.idealista.com/en/inmueble/106316721/`
* `https://www.idealista.it/en/immobile/30856200/`

---

## ✅ Sample Input

Only one field is required: a property URL.

```json
{
  "Url": "https://www.idealista.it/en/immobile/30856200/",
  "proxyConfig": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
  },
  "maxRetries": 2,
  "timeout": 30,
  "saveMapImages": true,
  "includeGallery": true,
  "extractContactInfo": true
}
```

---

## 📊 Sample Output

```json
{
  "id": "30856200",
  "Url": "https://www.idealista.it/en/immobile/30856200/",
  "title": "Villa for sale in Sud",
  "price": "2950000 €",
  "description": "In a valley between the Langhe and Monferrato areas, on the outskirts of Asti, there is this prestigious residential complex with 13.5 hectares of grounds for sale...",
  "location": "Asti",
  "characteristics": [
    "Villa",
    "1,750 m² built",
    "10 rooms",
    "9 bathrooms",
    "Terrace and balcony",
    "Garage and parking space included in the price",
    "Second hand/good condition",
    "Built in 1700",
    "Energy efficiency rating: (ECI not indicated)"
  ],
  "building": [],
  "energyPerformance": {},
  "amenities": [
    "Swimming pool",
    "Garden"
  ],
  "energyLabel": null,
  "updatedAt": "Listing updated 17 days ago",
  "MainImage": "https://img4.idealista.it/blur/WEB_DETAIL_TOP-L-L/0/id.pro.it.image.master/7c/38/32/671000685.jpg",
  "virtualTourUrl": null,
  "propertySpecs": {
    "rooms": 10,
    "constructedArea": 1750,
    "bathrooms": null,
    "garden": false,
    "pool": false,
    "terrace": false
  },
  "contactInfo": {
    "reference": "RIF.8291",
    "professionalName": "Lionard Luxury Real Estate",
    "location": "Firenze",
    "logo": "https://st3.idealista.it/09/5a/3a/lionard-luxury-real-estate.gif",
    "agencyWebsite": "https://idealista.it/en/pro/lionard-luxury-real-estate/",
    "contactMethods": {
      "chatAvailable": true,
      "phoneAvailable": true,
      "formAvailable": true
    },
    "ownerType": "agency",
    "mapLocation": null,
    "phones": "+39 055 093 1648"
  },
  "gallery": [
    {
      "url": "https://img4.idealista.it/blur/WEB_DETAIL/0/id.pro.it.image.master/c3/b3/08/671000686.jpg",
      "title": "Image Surroundings of villa in Sud",
      "description": "Surroundings",
      "tag": "Surroundings",
      "isPlan": false
    }
  ],
  "Map": {
    "src": "https://maps.googleapis.com/maps/api/staticmap?size=720x492&center=44.88689670%2C8.17289030&maptype=roadmap&channel=map_detail&scale=1&zoom=16&key=AIzaSyD-RjDXMztXd5rsu4zFG44V1kkMpdk3Hyc&signature=dRMZ7n5UatGmg-XwYgToqN2ERP4=",
    "title": "Map of the area",
    "addressVisibility": "HIDDEN"
  },
  "mapImagePath": "https://api.apify.com/v2/key-value-stores/undefined/records/30856200.jpg",
  "scrapedAt": "2025-07-03T10:25:28.408Z",
  "status": "success"
}
```

### 🖼️ **Live Results View**

![Idealista Scraper Results](path/to/your/screenshot.png)
*Real-time view of extracted property data in the Apify console*

---

## 🔧 Integration & Automation

### **API Integration**
This actor is designed to be called programmatically:

```javascript
// Example: Scraping multiple properties in a loop
const propertyUrls = [
  "https://www.idealista.it/en/immobile/30856200/",
  "https://www.idealista.com/en/inmueble/106316721/",
  "https://www.idealista.pt/en/imovel/33826216/"
];

for (const url of propertyUrls) {
  const run = await apifyClient.actor("dz_omar/idealista-scraper-api").call({
    Url: url,
    proxyConfig: { 
      useApifyProxy: true, 
      apifyProxyGroups: ["RESIDENTIAL"] 
    },
    maxRetries: 2,
    timeout: 30,
    saveMapImages: true,
    includeGallery: true,
    extractContactInfo: true
  });
  
  const { items } = await apifyClient.dataset(run.defaultDatasetId).listItems();
  console.log(items[0]); // Property data
}
```

### **Used by Bulk Scraper**
The **[Idealista Bulk Property Scraper](https://apify.com/dz_omar/idealista-scraper)** uses this API internally to:
1. Process search result pages
2. Navigate through property listings
3. Extract detailed data from each property
4. Aggregate results into comprehensive datasets

---

## 🎯 Output Data Structure

### **Key Fields Explained:**

* **`id`**: Unique property identifier from Idealista
* **`characteristics`**: Array of property features (size, rooms, condition, etc.)
* **`building`**: Building-specific features (elevator, parking, etc.)
* **`energyPerformance`**: Energy efficiency data object
* **`amenities`**: Property amenities (pool, garden, AC, etc.)
* **`propertySpecs`**: Structured specifications with boolean flags
* **`contactInfo`**: Complete agency information with contact methods
* **`gallery`**: Image array with titles, descriptions, and tags
* **`Map`**: Google Maps integration with coordinates
* **`mapImagePath`**: Path to saved map image in key-value store

---

## 💡 Who Is This For?

### **Single Property Analysis:**
* 🧑‍💼 Real estate agencies analyzing specific listings
* 📈 Investors evaluating individual properties
* 🔍 Content creators gathering specific property data
* 🤖 Developers building targeted automation
* 📱 Apps requiring individual property lookups

### **Bulk Operations:**
* 📊 Market analysts needing hundreds of properties → Use [Idealista Bulk Scraper](https://apify.com/dz_omar/idealista-scraper)
* 🏢 Agencies monitoring entire markets → Use [Idealista Bulk Scraper](https://apify.com/dz_omar/idealista-scraper)
* 📈 Investors tracking regional trends → Use [Idealista Bulk Scraper](https://apify.com/dz_omar/idealista-scraper)

---

## 📚 Configuration Options

### **Input Parameters:**
- **`Url`** (required): Single property URL to scrape
- **`proxyConfig`**: Proxy settings (RESIDENTIAL recommended)
- **`maxRetries`**: Number of retry attempts (default: 2)
- **`timeout`**: Request timeout in seconds (default: 30)
- **`saveMapImages`**: Save map images to storage (default: true)
- **`includeGallery`**: Extract image gallery (default: true)
- **`extractContactInfo`**: Include agency details (default: true)

### **Proxy Requirements**
Proxies are **required** for reliable operation. Recommended configuration:
```json
"proxyConfig": {
  "useApifyProxy": true,
  "apifyProxyGroups": ["RESIDENTIAL"]
}
```

---

## 💰 Pricing

### **Single Property Extraction:**
- **Actor Initialization**: $0.001 per run
- **Property Data Extracted**: $0.002 per successful extraction
- **Total**: $0.003 per property

### **Bulk Operations:**
For extracting multiple properties, consider the **[Idealista Bulk Scraper](https://apify.com/dz_omar/idealista-scraper)** which offers:
- One-time setup fee of $0.005
- Same $0.003 per property cost
- Automated workflow management
- Resume capability for large extractions

---

## ⚖️ Legal Considerations

This actor:
- Respects `robots.txt` directives
- Implements rate limiting to avoid server overload
- Only extracts publicly available data
- Does not bypass paywalls or login requirements
- Follows Idealista's terms of service

---

## 🤝 Support & Contact

For assistance or custom implementations:

* 📧 **Email**: [fridaytechnolog@gmail.com](mailto:fridaytechnolog@gmail.com)
* 🐙 **GitHub**: [DZ-ABDLHAKIM](https://github.com/DZ-ABDLHAKIM)
* 🐦 **Twitter**: [@DZ_45Omar](https://x.com/DZ_45Omar)
* 🔧 **Apify**: [dz_omar](https://apify.com/dz_omar)

---

## 🔗 Related Actors

- **[Idealista Bulk Property Scraper](https://apify.com/dz_omar/idealista-scraper)** - For extracting hundreds or thousands of properties in a single run

---

## 📋 Changelog

### **Version 1.0.0** (Current)
- ✅ Complete property data extraction
- ✅ Enhanced agency contact information
- ✅ Google Maps integration with image saving
- ✅ Rich image gallery with metadata
- ✅ Energy performance data
- ✅ Listing update tracking
- ✅ Robust error handling and retries
