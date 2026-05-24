# 🏠 SmartHostel — Student Hostel Management Website

A modern, responsive static website for student hostel management. Built with plain HTML, CSS, and JavaScript — ready for AWS S3 hosting and DevOps CI/CD pipelines.

## 📁 Project Structure

```
DevopsHostelapp/
├── index.html              # Home page
├── css/
│   └── style.css           # All styles (responsive + dark mode)
├── js/
│   └── main.js             # Theme toggle, nav, animations, forms
├── pages/
│   ├── facilities.html     # Facilities page
│   ├── booking.html        # Room booking page
│   ├── dashboard.html      # Student dashboard (UI)
│   ├── complaints.html     # Complaints & feedback
│   └── contact.html        # Contact us page
└── README.md
```

## 🚀 Pages

| Page | File | Description |
|------|------|-------------|
| Home | `index.html` | Hero, overview, room preview, announcements |
| Facilities | `pages/facilities.html` | Wi-Fi, Security, Laundry, Food, Study rooms |
| Room Booking | `pages/booking.html` | Room cards + booking form |
| Dashboard | `pages/dashboard.html` | Student info, fees, complaints (UI only) |
| Complaints | `pages/complaints.html` | Submit complaint + feedback form |
| Contact | `pages/contact.html` | Contact details, map, contact form, FAQ |

## ✨ Features

- ✅ Responsive design (mobile + desktop)
- ✅ Dark / Light mode toggle (persisted in localStorage)
- ✅ Smooth scroll animations (IntersectionObserver)
- ✅ Toast notifications on form submit
- ✅ Active nav link highlighting
- ✅ Hamburger menu for mobile
- ✅ Version badge in footer (easy to update per release)

## 🔧 Easy Content Updates (for CI/CD demos)

To simulate a new release, update any of these:

- **Version number**: Change `v1.0.0` → `v1.1.0` in all footer `version-badge` spans
- **Announcement banner**: Edit the `notice-banner` div in `index.html`
- **Room prices**: Update `room-price` divs in `booking.html` and `index.html`
- **Announcements**: Edit the announcement cards in `index.html`
- **Color theme**: Change `--primary` in `css/style.css`

## ☁️ AWS S3 Deployment

```bash
# Build (no build step needed — static files)
# Deploy to S3
aws s3 sync . s3://your-bucket-name --delete --exclude ".git/*"

# Enable static website hosting
aws s3 website s3://your-bucket-name --index-document index.html --error-document index.html
```

## 🔄 CI/CD Pipeline (GitHub Actions example)

```yaml
name: Deploy to S3
on:
  push:
    branches: [main, staging]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to S3
        run: aws s3 sync . s3://${{ secrets.S3_BUCKET }} --delete
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_DEFAULT_REGION: ap-south-1
```

## 🌿 Suggested Git Branching Strategy

```
main          → Production (v1.x.x)
staging       → Pre-production testing
feature/*     → New features (e.g. feature/online-payment)
hotfix/*      → Urgent fixes
release/*     → Release candidates
```

## 📦 Version History

| Version | Changes |
|---------|---------|
| v1.0.0 | Initial release — all 6 pages |

---
*SmartHostel © 2025 — Built for DevOps CI/CD demonstration*
