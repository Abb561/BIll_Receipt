# Car Removal Invoice Generator

A Progressive Web App (PWA) for generating professional invoices for Hamid Mukhtar Heavy & Light Trucks Transport - Dubai 24/7 Car Recovery & Towing Service.

## Features

- ✅ Offline functionality with Service Worker
- ✅ Installable as a standalone app
- ✅ Mobile-responsive design
- ✅ Print-friendly invoice generation
- ✅ No dependencies or build required
- ✅ Fast loading and caching

## Technology Stack

- HTML5
- CSS3
- JavaScript (Vanilla)
- Service Worker API
- Web App Manifest

## Project Structure

```
├── index.html          # Main invoice application
├── manifest.json       # PWA configuration
├── service-worker.js   # Offline caching strategy
├── icon-192.png        # App icon
├── typesignature.jpg   # Signature image
└── README.md          # This file
```

## Deployment Options

### Option 1: GitHub Pages (Recommended)
1. Push code to GitHub repository
2. Go to Settings → Pages
3. Select branch and folder (main/car-invoice-main)
4. Enable GitHub Actions for automatic deployment

**GitHub Actions** (`/.github/workflows/deploy.yml`):
- Automatically deploys on push to main branch
- No configuration needed, just enable in repository

### Option 2: Vercel (Free)
```bash
npm install -g vercel
vercel
```
Visit [vercel.com](https://vercel.com) and connect your GitHub repo.

### Option 3: Netlify (Free)
```bash
npm install -g netlify-cli
netlify deploy
```
Or connect via [netlify.com](https://netlify.com) GitHub integration.

### Option 4: Traditional Web Server (Apache/Nginx)
Simply copy all files to your web server's public directory.

### Option 5: AWS S3 + CloudFront
1. Create S3 bucket with public access
2. Upload all files
3. Configure CloudFront distribution
4. Set index.html as default root object

## Local Development

```bash
# No build step required - just serve the files
# Python 3
python -m http.server 8000

# Node.js (http-server)
npm install -g http-server
http-server

# Or use any local server of your choice
```

Then open `http://localhost:8000` in your browser.

## Features

### Invoice Generation
- Company branding and header
- Service details and pricing
- Customer information
- Digital signature support
- Print functionality

### PWA Features
- **Install**: Add to home screen on mobile or desktop
- **Offline**: Works without internet connection
- **Fast**: Instant loading with service worker caching
- **Full Screen**: Launches in standalone mode

## Service Worker

The app includes a service worker that:
- Caches essential assets on first visit
- Provides offline functionality
- Fetches fresh content when online
- Automatically updates when new version is deployed

## Browser Support

- Chrome/Edge 40+
- Firefox 44+
- Safari 11.3+
- Mobile browsers (iOS Safari 11.3+, Android Chrome 40+)

## Installation

### Mobile (Android/iOS)
1. Open in mobile browser
2. Tap menu (⋮) → "Install app" or "Add to Home Screen"
3. App will be installed like a native app

### Desktop (Chrome/Edge)
1. Click install icon (⬇️) in address bar
2. Or: Menu → "Install Car Invoice Generator"

## License

All rights reserved - Hamid Mukhtar Heavy & Light Trucks Transport

## Support

For issues or feature requests, contact the development team.
