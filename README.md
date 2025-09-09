# Landstro

<p align="center">
  <img src="landstro.png" alt="Landstro Logo" width="250" />
</p>

<p align="center">
  <strong>Modern landing page starter built with Astro, TailwindCSS, and TypeScript</strong>
</p>

<p align="center">
  <em>Landstro is offered by <a href="https://benav.io" target="_blank">benav.io</a></em>
</p>

Landstro is a feature-rich, production-ready landing page starter designed to help you quickly launch beautiful websites in minutes, not days. With dark mode, SEO optimization, contact forms, and built-in email collection, it provides everything you need to showcase your product, start collecting leads, and launch your business right away.

- To see what it looks like in practice, [click here](https://youtu.be/zMVpJUWaZso)!
- To understand why it was built, read our [7 Landing Page Mistakes Killing Your Conversions](https://www.benav.io/blog/7-landing-page-mistakes) blog post.

## Table of Contents

- [Features](#features)
- [Project Overview](#project-overview)
  - [Project Structure](#project-structure)
  - [Automated Build Process](#automated-build-process)
- [Getting Started: Technical Setup](#getting-started-technical-setup)
  - [Initial Installation](#initial-installation)
  - [Creating Environment Variables](#creating-environment-variables)
  - [Previewing and Building](#previewing-and-building)
- [Landing Page Components](#landing-page-components)
  - [Hero Section](#hero-section)
  - [Benefits Section](#benefits-section)
  - [Social Proof Section](#social-proof-section)
  - [Pricing Tables](#pricing-tables)
  - [FAQ Section](#faq-section)
- [Customization Guide](#customization-guide)
  - [Automatic Customizations](#automatic-customizations)
  - [Essential Files to Modify](#essential-files-to-modify)
  - [Advanced Customization](#advanced-customization)
- [Setting Up External Services](#setting-up-external-services)
  - [Domain Management](#domain-management)
  - [Email Communication with Postmark](#email-communication-with-postmark)
  - [Analytics with Google](#analytics-with-google)
- [Deployment Options](#deployment-options)
  - [Self-Hosted with Docker](#self-hosted-with-docker)
  - [Deploying on Digital Ocean](#deploying-on-digital-ocean)
  - [Setting Up Cloudflare](#setting-up-cloudflare)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Features

- 🚀 **Built with [Astro](https://astro.build/)** - Super fast static site generator
- 💨 **[TailwindCSS](https://tailwindcss.com/)** - Utility-first CSS framework
- 🌙 **Dark Mode** - Automatic and manual dark mode support
- 📱 **Responsive Design** - Mobile-first approach
- 🔍 **SEO Optimized** - Meta tags, Open Graph, JSON-LD, automatic sitemap generation
- 📧 **Contact Form** - Ready-to-use contact form with database storage
- 📊 **Waitlist & Early Access** - Built-in signup forms with database storage
- 📩 **Email Notifications** - Automatic contact and notifications with [Postmark](https://www.postmarkapp.com/?via=9f893f)
- 🔒 **Security Headers** - CSP, CORS, and other security best practices
- 📊 **Analytics Ready** - Google Analytics integration
- 🤖 **Automation** - Database initialization, image optimization, favicon generation, and more
- 🎨 **Modern UI Components**:
  - Hero Section
  - Features/Benefits
  - Social Proof
  - Pricing Tables
  - FAQ Section
  - Contact Modal
  - Footer
 
<br>
<a href="https://fastro.ai">
  <img width="1394" height="403" alt="fastroai-banner" src="https://github.com/user-attachments/assets/53db61f8-2fa7-46a2-ae91-8d131e0166d4" />
</a>
<br>

## Project Overview

### Project Structure

```
src/
├── components/     # Reusable UI components
├── layouts/        # Page layouts
├── pages/          # Route pages
├── lib/            # Utilities and database
├── styles/         # Global styles
└── data/           # Static data

public/
├── favicon/        # Favicon files (generated automatically)
├── images/         # Images and assets
│   ├── icon/       # Place your logo.png here
│   └── companies/  # Partner/client logos
```

### Built-in Automations

Landstro eliminates hours of tedious setup work with powerful built-in automations:

- **Database Setup**: Automatic SQLite initialization for contact forms and waitlist storage
- **Image Optimization**: All images are automatically compressed and converted to modern formats
- **Favicon Generation**: Complete favicon sets are created from your single logo file
- **Sitemap Creation**: SEO-friendly XML sitemap is generated during build
- **Security Headers**: Proper security configurations are automatically applied
- **Mobile Responsiveness**: All components are automatically responsive without extra work

These automations happen automatically during the build process (`npm run build`), saving you countless hours of configuration and optimization work that would normally be required when setting up a professional landing page.

For deployment, the `npm run prepare-prod` command creates a complete production build with all required files:

## Getting Started: Technical Setup

### Initial Installation

1. **Use the Landstro Template**:
   - Click the `Use this template` button in the GitHub repository
   - Create a repository using Landstro as your template
   - Clone your new repository:
   ```bash
   git clone https://github.com/yourusername/yourrepo.git
   cd yourrepo
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Add your logo**:
   - Create a `logo.png` file with your company logo
   - Place it in `public/images/icon/logo.png`
   - This logo will be used to generate all favicons and site branding
   - **Recommendation**: Use a square logo with at least 512×512px dimensions

### Creating Environment Variables

1. **Copy the example environment file**:
   ```bash
   cp env.example .env
   ```

2. **Update required settings**:
   ```env
   # Application Settings (Required)
   APP_NAME=Your Company Name
   APP_DOMAIN=your-domain.com
   SITE_URL=https://your-domain.com
   ADMIN_EMAIL=your-email@example.com
   ```

3. **Configure optional features**:
   ```env
   # Contact Form Settings (Optional)
   CONTACT_FORM_ENABLED=true  # Set to false to disable
   CONTACT_FORM_NOTIFY_EMAIL=your-email@example.com

   # Waitlist Settings (Optional)
   WAITLIST_ENABLED=true  # Set to false to disable
   WAITLIST_NOTIFY_EMAIL=your-email@example.com

   # Email Notifications via Postmark (Optional)
   POSTMARK_API_KEY=your_postmark_api_key_here  # Leave empty to disable email notifications
   POSTMARK_FROM=no-reply@your-domain.com
   POSTMARK_TO=support@your-domain.com

   # Analytics (Optional)
   GOOGLE_ANALYTICS_ID=G-XXXXXXXXXX  # Leave empty to disable analytics
   ANALYTICS_DOMAINS=https://www.googletagmanager.com https://www.google-analytics.com

   # Social Media Links (Optional)
   # Omit or leave empty to hide the corresponding social media icons
   GITHUB_URL=https://github.com/your-company
   LINKEDIN_URL=https://linkedin.com/company/your-company
   TWITTER_URL=https://twitter.com/your_company
   FACEBOOK_URL=https://facebook.com/your-company
   INSTAGRAM_URL=https://instagram.com/your_company

   # Feature Flags (Optional)
   ENABLE_NAVBAR=true  # Set to false to hide the navigation bar

   # Pricing (in USD, Optional)
   # Set to "FREE" to display a free tier
   # Leave empty or omit to display "Contact Us" instead of a price
   PRICE_BASIC=9
   PRICE_PRO=29
   PRICE_ENTERPRISE=99
   
   # Pricing Tier Names (Optional)
   BASIC_TIER_NAME=Basic
   PRO_TIER_NAME=Pro
   ENTERPRISE_TIER_NAME=Enterprise
   
   # Deployment (Optional)
   MAINTAINER=Your Name
   CREATOR=Your Company Name
   ```

Note: Most features can be toggled on/off through these environment variables without changing code. The database will be automatically initialized based on which features you enable.

### Previewing and Building

1. **Preview your site locally**:
   ```bash
   npm run dev
   ```

2. **Build for production**:
   ```bash
   npm run build
   ```

## Landing Page Components

Landstro includes several pre-built components that you can customize to create an effective landing page.

### Hero Section

The hero section (`src/components/Hero.astro`) is the first thing visitors see on your landing page:

- Headline and subheadline for your value proposition
- Primary and secondary call-to-action buttons
- Optional product demonstration image or video
- Trust indicators such as client logos or testimonials

### Benefits Section

The benefits section (`src/components/Benefits.astro`) showcases your product's key advantages:

- Icon-based feature highlights
- Concise benefit descriptions
- Organized in a responsive grid layout
- Optional statistics or metrics

### Social Proof Section

The social proof section (`src/components/SocialProof.astro`) builds credibility:

- Customer testimonials with attribution
- Partner or client logos
- User statistics and metrics
- Optional integration with review platforms

### Pricing Tables

The pricing section (`src/components/Pricing.astro`) presents your pricing options:

- Multiple pricing tiers with feature comparison
- Highlighted recommended plan
- Monthly/annual toggle option
- Custom enterprise option with CTA

### FAQ Section

The FAQ section (`src/components/FAQ.astro`) addresses common questions:

- Expandable accordion-style questions and answers
- Categorized questions for easier navigation
- Call-to-action for additional support
- Customizable layout and styling

## Customization Guide

### Automatic Customizations

The build process automatically handles several customizations based on your `.env` settings:

1. **Company Name and Branding**: Set via environment variables:
   - `APP_NAME` - Updates the navbar brand name and SEO metadata site name
   - `COMPANY_TAGLINE` - Updates the main headline in the hero section
   - Various references throughout the site use these values

2. **Social Media Links**: Set via environment variables to appear in the navbar and footer:
   - Each platform will only be displayed if a URL is provided
   - Omitting or leaving empty any platform will hide its icon
   - Supported platforms: `TWITTER_URL`, `LINKEDIN_URL`, `GITHUB_URL`, `FACEBOOK_URL`, `INSTAGRAM_URL`

3. **UI Components**: Control which components are displayed:
   - `ENABLE_NAVBAR=false` - Hide the full navigation bar but still show the logo/brand in the top-left corner
   - Other feature flags can control additional components

4. **Email Settings**: Set via Postmark API keys and notification emails in `.env` - these configure form submissions

5. **Pricing Tables**: Customized via environment variables:
   - Set pricing with `PRICE_BASIC`, `PRICE_PRO`, and `PRICE_ENTERPRISE`
   - Use "FREE" to display a free tier (e.g., `PRICE_BASIC=FREE`)
   - Leave empty or omit variables to show "Contact Us" instead of a price
   - Customize tier names with `BASIC_TIER_NAME`, `PRO_TIER_NAME`, and `ENTERPRISE_TIER_NAME`

6. **Favicons**: Automatically generated from your logo.png during build

7. **Database**: Automatically initialized with proper tables for waitlist/contact forms

### Essential Files to Modify

1. **Branding & Logo**:
   - Replace `public/images/icon/logo.png` with your own logo (a square PNG, at least 512×512px)
   - Remove or replace company logos in `public/images/companies/` with your own partners/clients
   - All optimized images and favicons will be regenerated automatically when source images change

2. **Content Sections** (Manual Updates Required):
   - Hero section: `src/components/Hero.astro` (update headlines, descriptions, CTAs)
   - Benefits/features: `src/components/Benefits.astro` (update your product features)
   - Pricing: `src/components/Pricing.astro` (update tiers and pricing)
   - FAQ: `src/components/FAQ.astro` (update questions and answers)
   - Call to action: `src/components/CTA.astro` (update to match your value proposition)
   - Footer: `src/components/Footer.astro` (update copyright and additional links)

3. **Environment Variables** (Critical Configuration):
   - Update your `.env` file with all necessary values (see [Environment Variables](#creating-environment-variables) section)
   
4. **SEO & Metadata**:
   - Edit `src/layouts/Layout.astro` to update JSON-LD structured data (manually)
   - Meta keywords tag in `src/components/SEOMetadata.astro` should be updated manually

### Advanced Customization

- **Colors & Theme**: Edit the color scheme in `tailwind.config.mjs`
- **Typography**: Modify font settings in `tailwind.config.mjs`
- **Layout**: Adjust container widths and spacing in relevant component files
- **Astro Config**: Modify `astro.config.mjs` to adjust site settings, integrations, and image optimization
- **Custom Components**: Create your own components in the `src/components` directory and import them in your pages:
  ```astro
  ---
  // src/components/YourCustomComponent.astro
  const { title, description } = Astro.props;
  ---
  
  <div class="my-custom-component">
    <h2>{title}</h2>
    <p>{description}</p>
  </div>
  ```
  
  Then use it in any page:
  ```astro
  ---
  import YourCustomComponent from '../components/YourCustomComponent.astro';
  ---
  
  <YourCustomComponent title="Custom Feature" description="This is my custom component" />
  ```
- **Extending Existing Components**: You can extend existing components by copying them to a new file and modifying as needed, or by using Astro's slot system for composition
- **Deployment Variables**: Set `MAINTAINER` and `CREATOR` in the `.env` file to customize deployment information in Docker configurations

## Setting Up External Services

### Domain Management

#### Recommended Domain Types

- **Use**: `.com`, `.io`, `.ai`, `.dev`, or regional TLDs (`.co.uk`, `.de`, etc.)
- **Avoid**: Lesser-known TLDs like `.xyz`, `.online`, `.site` or even `.net` which can appear less professional

#### Domain Name Best Practices

- **Keep it short**: Ideally under 15 characters
- **Make it memorable**: Easy to spell and pronounce
- **Avoid hyphens**: They reduce memorability and trustworthiness
- **Check availability**: Ensure matching social media handles are available

#### Purchasing Process

1. Visit [Namecheap](namecheap.pxf.io/bO5rQv) or your preferred registrar
2. Search for your desired domain name
3. Purchase for 1-2 years
4. Enable privacy protection to hide your personal information

### Email Communication with [Postmark](https://www.postmarkapp.com/?via=9f893f)

This step is optional (and requires a work email). If you don't pass a Postmark key to `Landstro`, it will just store the emails in the database without sending notifications. You can also change the implementation for your preferred email sending provider.

1. **Create a Postmark account**:
   - Sign up at [Postmark](https://www.postmarkapp.com/?via=9f893f)
   - Verify your domain ownership through DNS records

2. **Create a new server in Postmark**:
   - Name it after your website/project
   - Configure sender signatures for your domain

3. **Get your API keys**:
   - Navigate to "API Tokens" in your server settings
   - Copy the Server API token
   - Note: Keep this key private; never commit it to public repositories

4. **Configure DKIM and SPF records**:
   - Follow Postmark's instructions to add DNS records
   - This improves email deliverability and prevents spam flags

### Analytics with Google

1. **Create a Google Analytics 4 account**:
   - Visit [Google Analytics](https://analytics.google.com/)
   - Click "Start measuring" and follow the setup process

2. **Create a property for your website**:
   - Name it after your domain
   - Set the reporting time zone appropriately

3. **Set up a data stream**:
   - Choose "Web" as the platform
   - Enter your website URL
   - Note the Measurement ID (starts with "G-")

4. **Enable recommended data collection features**:
   - Enhanced measurement for events
   - User metrics reports

## Deployment Options

### Self-Hosted with Docker

Landstro includes a convenient deployment script that handles the entire process:

```bash
# Make the script executable (first time only)
chmod +x deploy.sh

# Run deployment
./deploy.sh
```

The script will:

1. Load environment variables from your `.env` file
2. Prepare your production build with `npm run prepare-prod`
3. Set up Docker containers
4. Verify SSL configuration
5. Provide status of your deployment

For manual deployment, you can also run:

```bash
# Generate production assets
npm run prepare-prod

# Deploy using Docker
cd production-build
docker-compose -f ../docker-compose.yml up -d
```

### Deploying on Digital Ocean

1. **Create a Digital Ocean account**:
   - Sign up at [Digital Ocean](https://www.digitalocean.com/)
   - Add a payment method

2. **Create a new Droplet**:
   - Choose Ubuntu 22.04 LTS (or the newest LTS)
   - Select a Basic plan ($5-10/month is sufficient to host several landing pages)
   - Choose a datacenter region closest to your target audience
   - Add your SSH key for secure access

3. **Connect to your Droplet**:
   ```bash
   ssh root@your-droplet-ip
   ```

   *Or just click the `console` button in your droplet page.*

4. **Install Docker and Docker Compose**:
   ```bash
   apt update
   apt install -y docker.io docker-compose
   ```

5. **Configure your server**:
   ```bash
   mkdir -p /var/www/yourrepo # or the name of your landing page
   cd /var/www/yourrepo
   ```

6. **Copy your files to the server**:
   Using Git:
   
   ```bash
   # On your server

   # use your username and repository name here
   git clone https://github.com/yourusername/yourrepo.git .
   ```

7. **Set up environment variables**:
   ```bash
   # On your server
   cp env.example .env
   nano .env  # Edit with your values
   ```

8. **Run the deployment script**:
   ```bash
   chmod +x deploy.sh
   ./deploy.sh
   ```

9. **Verify deployment**:
   - Check if containers are running: `docker compose ps`
   - View logs if needed: `docker compose logs -f`

10. **Server IP**:
   - In the droplet page, you will see a number like this: `ipv4: 12.34.567.89`, save this for later

### Setting Up Cloudflare

1. **Create a Cloudflare account**:
   - Sign up at [Cloudflare](https://www.cloudflare.com/)
   - Add your domain to Cloudflare

2. **Update nameservers at your domain registrar**:
   - Find the Cloudflare nameservers provided during setup
   - Update your domain's nameservers at your registrar ([tutorial for Namecheap here](https://namecheap.pxf.io/EE2PJD))
   - Wait for DNS propagation (can take 24-48 hours, usually takes less)

3. **Configure DNS records in Cloudflare**:
   - Create an A record pointing to your server IP (the one you saw as `ipv4`):
     ```
     Type: A
     Name: @ (or the root domain itself e.g., `benav.io`)
     Content: your-server-ip (e.g., 12.34.567.89)
     Proxy status: Proxied
     ```
     
     This creates a record for your root domain (e.g., `benav.io`).
   
   - Add a CNAME record for www subdomain:
     ```
     Type: CNAME
     Name: www
     Content: your-root-domain (e.g., benav.io)
     Proxy status: Proxied
     ```
     
     This creates a record for the www version (e.g., `www.benav.io`).

4. **Enable SSL/TLS protection**:
   - Go to SSL/TLS
   - In **overview**, set SSL/TLS encryption mode to "Full (strict)"
   - In **Edge Certificates**, disable "Always Use HTTPS" (caddy will handle this)
   - Turn off "Automatic HTTPS Rewrites" (caddy also handles this)

5. **Configure Cloudflare settings**:
   - Turn on caching features appropriate for your site

6. **Verify configuration**:
   - Visit your domain to ensure it loads properly
   - Check SSL certificate is valid (look for the padlock in browser)

## Troubleshooting

Common issues and solutions:

- **Missing favicons**: Ensure your logo.png exists at `public/images/icon/logo.png`
- **Form not working**: Check that the database was properly initialized during build
- **Image optimization issues**: Ensure Sharp is installed correctly
- **Site URL issues**: Verify that the `SITE_URL` environment variable is set correctly in your `.env` file
- **Failed deployment**: Check Docker logs with `docker-compose logs -f`
- **SSL certificate issues**: Verify Cloudflare is properly configured with your domain

> **Note about image regeneration**: When changing the logo.png or other source images, the build process automatically detects changes and regenerates optimized images and favicons as needed. No manual deletion of previously generated files is required.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Benav Labs – [benav.io](https://benav.io)
[github.com/benavlabs](https://github.com/benavlabs/)

<hr>
<a href="https://benav.io">
  <img src="https://github.com/benavlabs/fastcrud/raw/main/docs/assets/benav_labs_banner.png" alt="Powered by Benav Labs - benav.io"/>
</a>
