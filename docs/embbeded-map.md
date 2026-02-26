# Embedding Kohesio Map

## Domain Whitelisting & CORS Security

Before embedding the map into your website, you must **whitelist the target domain or subdomain** to comply with **Cross-Origin Resource Sharing (CORS)** security policies. This ensures that the browser allows the map to fetch necessary data and assets from the server.

To complete this procedure:
* **Action:** Send an email to the responsible team to request whitelisting.
* **Recipient:** [REGIO-KOHESIO@ec.europa.eu](mailto:REGIO-KOHESIO@ec.europa.eu)
* **Details to Include:** Specify the exact domain or subdomain where the map will be embedded (e.g., `https://portal.yourdomain.eu`).

> **Warning:** If the domain is not whitelisted, the map will fail to render, and the browser will trigger a CORS block error in the developer console.

## Domain Identification

For the server to correctly identify the origin of embedding requests, the website embedding the map must provide its domain through **one of the following methods**:

### Option 1 — Request Headers (automatic in most browsers)

Ensure your website sends either the `Referer` or the `Origin` HTTP header when loading the map. Modern browsers do this automatically for embedded content, but verify that your server or Content Security Policy does not suppress these headers (e.g., via `Referrer-Policy: no-referrer`).

| Header | Example value |
|--------|--------------|
| `Referer` | `https://portal.yourdomain.eu/page` |
| `Origin` | `https://portal.yourdomain.eu` |

### Option 2 — `embed` Query Parameter

If headers cannot be relied upon (e.g., due to a strict referrer policy), append the `embed` query parameter to the map URL with your domain as the value:

```html
<embed type="text/html"
  src="https://kohesio.ec.europa.eu/en/map?embed=portal.yourdomain.eu"
  width="800" height="800">
```

> **Note:** At least one of these two methods must be in place. Without a recognisable origin, the server may be unable to attribute traffic correctly and access could be restricted.

## Embedding the map

You can embed the kohesio map into your website, just use the code snippet bellow and customize using the parameters.

- Please use the parameter embed=portal.yourdomain.eu for us to understand from where the traffic is coming

```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?embed=portal.yourdomain.eu"  width="800" height="800">
```

## Languages

The kohesio map supports all EU languages:

- French version
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/fr/map?embed=portal.yourdomain.eu"  width="800" height="800">
```

- Greek version
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/el/map?embed=portal.yourdomain.eu"  width="800" height="800">
```

## Parameters

You can customize the map visualization using the following parameters:

- mapRegion - To drill-down in a specific region into the map (default is empty, it means the whole Europe)
- heatScale - To see the map with a heat scale per region (default is false)
- hideProjectsNearBy - To hide the "Projects near me" button (default is false)
- coords - To show a specific popup in a certain coordinate (default is empty), this parameter depends on the mapRegion parameter 
- openProjectInner - To show the project detail inside the map window (default is false, it means the projects will open in a new tab window)
- project - It will open the project directly in a popup (default is empty). This parameter depends on the openProjectInner set to true
- clusterView - To show the projects in a cluster view (default is false) if not set, the projects will be shown in a region view
- cci - "Common Identification Code". It will take priority over the others parameters and will show only the coordinates for this particular cci
- fund - Fund this project was financed from (ex: https://linkedopendata.eu/entity/Q2504369)

## Example:

### Pass multiple CCI parameters with the name "cci"
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?cci=2014PL16M2OP005,2014PL16M2OP008"  width="800" height="800">
```

### Drill-down region
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?embed=portal.yourdomain.eu&mapRegion=Q2556199&coords=-8.3211792431454,40.1552222"  width="800" height="800">
```

### Drill-down region with coordinates selection
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?embed=portal.yourdomain.eu&mapRegion=Q2556199&coords=-8.3211792431454,40.1552222"  width="800" height="800">
```

### Drill-down into a region with heat scale
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?embed=portal.yourdomain.eu&?heatScale=true&mapRegion=Q2556137"  width="800" height="800">
```
## Filters
The map supports the following filters:
- keywords
- town
- country
- region
- projectCollection
- theme
- fund

```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?country=Belgium"  width="800" height="800">
```

### embed map with cluster view
```html
<embed type="text/html" src="https://kohesio.ec.europa.eu/en/map?clusterView=true"  width="800" height="800">
```
