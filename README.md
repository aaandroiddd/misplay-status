# misplay.gg Status Page

An independent status page for misplay.gg, hosted separately from the main application to remain accessible during outages.

## Deployment

### GitHub Pages (Recommended)

1. Create a new repository on GitHub (e.g., `misplay-status`)

2. Push this code:
   ```bash
   cd misplay-status
   git init
   git add .
   git commit -m "Initial status page"
   git remote add origin git@github.com:YOUR_USERNAME/misplay-status.git
   git push -u origin main
   ```

3. Enable GitHub Pages:
   - Go to repository Settings > Pages
   - Source: Deploy from a branch
   - Branch: `main` / `/ (root)`
   - Save

4. Your status page will be live at: `https://YOUR_USERNAME.github.io/misplay-status/`

### Custom Domain (status.misplay.gg)

1. Add a `CNAME` file with your domain:
   ```
   status.misplay.gg
   ```

2. In your DNS provider, add a CNAME record:
   - Name: `status`
   - Value: `YOUR_USERNAME.github.io`

3. In GitHub Pages settings, enter your custom domain

## Updating Status

Edit `index.html` directly to update:

### Change Overall Status

Find the status banner and update:
```html
<!-- Operational -->
<span class="status-dot operational"></span>
All Systems Operational

<!-- Degraded -->
<span class="status-dot degraded"></span>
Degraded Performance

<!-- Outage -->
<span class="status-dot outage"></span>
Service Disruption
```

### Update Service Status

Find the service and change the class:
```html
<span class="dot operational"></span>  <!-- Green -->
<span class="dot degraded"></span>     <!-- Yellow -->
<span class="dot outage"></span>       <!-- Red -->
```

### Add an Incident

Uncomment and modify the incident template:
```html
<div class="incident">
  <div class="incident-header">
    <div>
      <h3 class="incident-title">Your Incident Title</h3>
      <span class="incident-date">December 29, 2025</span>
    </div>
    <span class="incident-status investigating">Investigating</span>
  </div>
  <p class="incident-body">
    Description of what's happening and what you're doing about it.
  </p>
</div>
```

Status options: `resolved`, `investigating`

## Why Separate Hosting?

This status page is hosted independently from the main misplay.gg application so that:

1. **Always Accessible** - If Vercel/main hosting goes down, users can still check status
2. **No Dependencies** - Pure static HTML with no external dependencies
3. **Fast Loading** - Minimal page weight, loads instantly
4. **Easy Updates** - Edit HTML directly, no build process needed
