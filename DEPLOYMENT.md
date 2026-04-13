# Deployment Guide

## Quick Start

This is a static PWA with no build dependencies. Deploy anywhere that serves static files.

## Deployment Checklist

- [ ] Update CNAME in GitHub Actions workflow to your domain
- [ ] Enable GitHub Pages in repository settings
- [ ] Test offline functionality after deployment
- [ ] Verify service worker installation
- [ ] Test on mobile devices
- [ ] Update manifest.json if changing domain

## Step-by-Step Deployment

### GitHub Pages (Recommended)

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Add deployment configurations"
   git push -u origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings
   - Scroll to "Pages"
   - Select "Deploy from a branch"
   - Choose: main branch, /root or /docs folder
   - Or use GitHub Actions (automatic)

3. **Your site will be live at:**
   ```
   https://[github-username].github.io/car-invoice
   ```

4. **Custom Domain (Optional)**
   - Update `CNAME` in `.github/workflows/deploy.yml`
   - Add DNS records pointing to GitHub Pages
   - Update manifest.json with new URL

### Vercel Deployment

1. **Install Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **Deploy**
   ```bash
   vercel
   ```

3. **Configure**
   - Connect to GitHub repository
   - Set build command: `echo 'Static site'`
   - Set output: `.`

### Netlify Deployment

1. **Option A: CLI**
   ```bash
   npm install -g netlify-cli
   netlify deploy --prod
   ```

2. **Option B: Git Integration**
   - Connect GitHub repo at netlify.com
   - Netlify auto-deploys on push

3. **Configure**
   - Build command: empty
   - Publish directory: `.`

### Docker Deployment

```dockerfile
FROM nginx:alpine
COPY car-invoice-main/ /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Deploy:
```bash
docker build -t car-invoice .
docker run -p 80:80 car-invoice
```

## Environment Configuration

Update these in `manifest.json` and `index.html` if needed:

- `start_url`: Main entry point
- `theme_color`: Browser UI color
- `background_color`: Splash screen color
- `canonical_url`: For SEO and PWA manifests

## Testing Deployment

After deployment:

1. **Check PWA Installation**
   - Chrome: ⋮ menu → "Install app"
   - Firefox: ⋮ menu → "Install"
   - Safari: Share → "Add to Home Screen"

2. **Test Offline Mode**
   - Open DevTools (F12)
   - Application → Service Workers
   - Check "Offline"
   - Reload page - should still work

3. **Verify Service Worker**
   - DevTools → Application → Service Workers
   - Should show active and running

4. **Check Manifest**
   - DevTools → Application → Manifest
   - Verify all properties are correct

## Troubleshooting

### Service Worker Not Updating
- Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)
- Clear cache: DevTools → Application → Clear storage

### CORS Issues
- Ensure all CDN resources are loaded over HTTPS
- Check font loading from Google Fonts

### PWA Not Installing
- Must be HTTPS (exception: localhost)
- Service worker must be registered
- manifest.json must be valid

### Build Errors
- This is a static site - no build needed
- If using CI/CD, ensure files aren't being modified

## Monitoring

- Check browser console for service worker errors
- Monitor Network tab for 404s
- Use Lighthouse audit in DevTools
- Monitor Core Web Vitals

## Rollback

If issues occur:

```bash
# GitHub Pages
git revert [commit-hash]
git push

# Vercel/Netlify
- Rollback via dashboard
- Or re-deploy previous commit
```

## Performance Optimization

- [ ] Minimize image sizes (use TinyPNG)
- [ ] Minify CSS/JavaScript if adding any
- [ ] Enable GZIP compression on server
- [ ] Use CDN for assets
- [ ] Monitor Core Web Vitals

## Security

- [ ] Enable HTTPS everywhere
- [ ] Set security headers (Content-Security-Policy)
- [ ] Regular security audits
- [ ] Keep dependencies updated
- [ ] Monitor for vulnerabilities

## Additional Resources

- [PWA Documentation](https://web.dev/progressive-web-apps/)
- [Service Worker Guide](https://developer.mozilla.org/docs/Web/API/Service_Worker_API)
- [Web App Manifest](https://developer.mozilla.org/docs/Web/Manifest)
