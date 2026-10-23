# CanineCost UK - Setup & Customisation Guide

A turnkey, responsive, VAT-inclusive canine surgery cost estimator for UK veterinary practices and pet care businesses.

## 🚀 Quick Start (Under 2 Minutes)

- **Preview Locally:** Double-click `index.html` to open it in any web browser. You do not need Node.js, npm, or a local server.
- **Customise:** Open `config.js` in any text editor (Notepad, TextEdit, VS Code) to update your practice name, phone number, and pricing.
- **Save & Refresh:** Save `config.js` and refresh `index.html` in your browser to see your changes instantly.

## ⚙️ How to Adjust Everything in config.js

All settings live inside `config.js`. You never need to touch the HTML or CSS.

### 1. Practice Branding & Contact Details

Locate the `branding` section at the top of `config.js`:

```javascript
branding: {
  siteName: "Acorn Vets",                      // Displays in header, footer, and browser tab
  logoUrl: "logo.png",                         // Image path (PNG/SVG) or leave "" for default paw icon
  primaryColor: "#0f766e",                     // Main brand hex color
  primaryDark: "#115e59",                      // Slightly darker shade for button hover states
  primaryLight: "#f0fdf4",                     // Very light shade for background highlights
  operatorName: "Acorn Veterinary Group Ltd",  // Legal entity name in footer & disclaimers
  contactEmail: "info@acornvets.co.uk",        // Injected into privacy standards & mailto links
  emergencyPhone: "01453 123 456",             // Clinic phone number
  bookingUrl: "https://acornvets.co.uk/book",  // Link for appointment booking CTA
  emergencyBannerText: "..."                   // Top warning text (leave default recommended)
}
```

- **Custom Logo:** Save your logo file (e.g. `logo.png`) inside this folder and set `logoUrl: "logo.png"`. Leave it as `""` to use the built-in clean SVG paw icon.
- **Brand Colors:** Change the `primaryColor` hex codes to match your clinic's brand guidelines. The site will instantly update all buttons, borders, and highlights.

### 2. Adjusting Pricing

You have two ways to adjust prices:

#### A. Overall Regional Multiplier (Fastest)

If your practice charges slightly above or below national averages, adjust your postcode in `postcodeMultipliers`:

```javascript
postcodeMultipliers: {
  "GL": 1.00,  // 1.00 = baseline average
  "B": 0.95,   // 5% cheaper than baseline
  "SW": 1.35   // 35% higher to reflect London overheads
}
```

Changing a multiplier dynamically scales all procedure totals and line items across the entire tool.

#### B. Per-Procedure Base Price Tuning

To change the cost of a specific operation, locate the procedure in the `procedures` array:

```javascript
{
  id: "tplo",
  name: "Torn Knee Ligament Surgery (Cruciate Repair / TPLO)",
  category: "ORTHOPEDIC",
  basePrice: 3200,   // <-- Update this master figure (Includes VAT)
  emergency: false,
  desc: "...",
  recovery: "8 to 12 weeks...",
  lineItems: [
    { name: "Pre-surgery blood test and health check", price: 150 },
    { name: "Full general anaesthetic and monitoring", price: 380 },
    // Adjust individual line items here if desired
  ]
}
```

- **VAT Note:** All base prices and line items are statutory 20% VAT-inclusive.
- **Dog Weight Scaling:** The tool automatically adjusts prices on screen using industry-standard weight factors:
  - Toy (<5kg): ×0.8
  - Small/Med (5–20kg): ×1.0 (baseline)
  - Large (20–40kg): ×1.3
  - Giant (>40kg): ×1.6

### 3. Adding or Deleting Procedures

- **To remove a procedure:** Delete the entire object block `{ ... },` from the `procedures` list.
- **To add a procedure:** Copy an existing procedure block, paste it at the end of the array, give it a unique `id`, and assign one of the five recognized categories:
  - `"ORTHOPEDIC"`
  - `"SOFT_TISSUE"`
  - `"EMERGENCY"`
  - `"OPHTHALMIC"`
  - `"DENTAL"`

## 🌐 Deploying to the Web

### Free 1-Click Hosting (Netlify or Vercel)
1. Go to Netlify Drop or Vercel.
2. Drag and drop this entire template folder into the browser window.
3. Your site is live on a custom URL in seconds.

### Adding to an Existing WordPress or Custom Site
- **As a Subdomain:** Deploy the folder to `pricing.yourpractice.co.uk` and link to it from your main site menu.
- **In an iframe:** Embed `<iframe src="https://pricing.yourpractice.co.uk" width="100%" height="900" frameborder="0"></iframe>` on any existing WordPress page.

## ⚖️ UK Regulatory & Compliance Notice

Under the CMA Veterinary Services Market Investigation Order 2026, UK veterinary practices are required to provide transparent, accessible price guidance for common and urgent treatments.

- This estimator demonstrates pricing transparency before clinical consultations.
- All displayed estimates include UK VAT.
- An emergency triage alert banner is permanently displayed to ensure owners of critically ill pets do not delay in-person emergency care.

## 📄 License & Terms

- **License:** Single-use commercial license. You are licensed to use, modify, and host this template for one business/domain. You may not resell or redistribute the source code.
- **Support:** Provided on an as-is, self-hosted basis. No recurring technical support is included.
- **Digital Download Policy:** In accordance with the UK Consumer Contracts Regulations 2013, digital downloads lose right of withdrawal once file delivery has commenced.
