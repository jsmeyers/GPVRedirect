# GPVRedirect

Static redirect site for the City of Lowell GIS parcel viewer.

All traffic — including subpages — is permanently redirected (301) to:

**https://www.axisgis.com/lowellma**

## How it works

- `staticwebapp.config.json` — Azure Static Web Apps configuration with a wildcard route (`/*`) that 301-redirects all requests to AxisGIS. This handles both the root URL and any subpage paths.
- `index.html` — Fallback meta-refresh redirect in case the routing config doesn't catch a request.

## Deployment

Deploy as an Azure Static Web App. The `staticwebapp.config.json` file must be in the root of the deployed output directory.

## Adding more routes

Edit `staticwebapp.config.json` and add entries to the `routes` array. More specific routes should come before the `/*` wildcard.

```json
{
  "routes": [
    {
      "route": "/specific-page",
      "redirect": "https://example.com/specific",
      "statusCode": 301
    },
    {
      "route": "/*",
      "redirect": "https://www.axisgis.com/lowellma",
      "statusCode": 301
    }
  ]
}
```