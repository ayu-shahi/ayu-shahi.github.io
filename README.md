# Ayush Shahi - Personal Website

A clean, modern personal academic website built with [Astro](https://astro.build).

## Project Structure

```
personal-website/
├── public/
│   ├── images/
│   │   ├── profile.jpg          # Your profile photo
│   │   └── personal/            # Personal page images
│   │       ├── travel-1.jpg
│   │       ├── travel-2.jpg
│   │       └── travel-3.jpg
│   └── favicon.svg
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro     # Main layout template
│   ├── pages/
│   │   ├── index.astro          # Home page
│   │   ├── research.astro       # Research page
│   │   ├── cv.astro             # CV page
│   │   └── personal.astro       # Personal page
│   └── styles/
│       └── global.css           # Global styles
├── .github/
│   └── workflows/
│       └── deploy.yml           # GitHub Pages deployment
├── astro.config.mjs             # Astro configuration
├── package.json
└── README.md
```

## Prerequisites

- [Node.js](https://nodejs.org/) version 18 or higher
- [Git](https://git-scm.com/) installed on your computer
- A [GitHub](https://github.com/) account

## Local Development

### 1. Install Dependencies

Open a terminal in the project folder and run:

```bash
npm install
```

### 2. Start Development Server

```bash
npm run dev
```

The site will be available at `http://localhost:4321`.

### 3. Build for Production

```bash
npm run build
```

This creates a `dist/` folder with your static site.

### 4. Preview Production Build

```bash
npm run preview
```

## Adding Your Content

### Profile Photo

1. Add your profile photo as `public/images/profile.jpg`
2. Recommended size: 400x400 pixels or larger (square aspect ratio)

### Personal Page Images

1. Add images to `public/images/personal/`
2. Name them `travel-1.jpg`, `travel-2.jpg`, etc. (or update the filenames in `src/pages/personal.astro`)
3. Recommended size: 800x600 pixels or larger

### CV PDF Link

1. Upload your CV to Google Drive (or another hosting service)
2. Update the link in:
   - `src/pages/index.astro` (contact links section)
   - `src/pages/cv.astro` (download link)

### Research Papers

Edit `src/pages/research.astro` to add your papers. Each paper entry follows this template:

```html
<article class="paper-entry">
  <h3 class="paper-title">
    Paper Title Here
    <span class="paper-links">
      <a href="link-to-pdf">[PDF]</a>
      <a href="link-to-appendix">[Appendix]</a>
    </span>
  </h3>
  <p class="paper-authors">Author 1, Author 2</p>
  <p class="paper-venue">Journal Name, Year</p>
  <button class="abstract-toggle" onclick="toggleAbstract('abstract-X')">
    <span class="arrow">&#9660;</span> Abstract
  </button>
  <div id="abstract-X" class="abstract-content">
    <p>Your abstract text here...</p>
  </div>
</article>
```

## Deploying to GitHub Pages

### Step 1: Create a GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon in the top-right corner and select **New repository**
3. Name your repository (e.g., `personal-website`)
4. Choose **Public** (required for free GitHub Pages)
5. **Do NOT** initialize with README, .gitignore, or license (you already have files)
6. Click **Create repository**

### Step 2: Update Astro Configuration

Edit `astro.config.mjs` to match your GitHub username and repository name:

```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://YOUR-USERNAME.github.io',
  base: '/YOUR-REPO-NAME',
  output: 'static',
});
```

**Example:** If your GitHub username is `ayushshahi` and repo is `personal-website`:

```javascript
site: 'https://ayushshahi.github.io',
base: '/personal-website',
```

**For a custom domain or username.github.io repo:** If you want your site at `username.github.io` (not `username.github.io/repo-name`), name your repo `username.github.io` and set:

```javascript
site: 'https://username.github.io',
base: '/',
```

### Step 3: Initialize Git and Push to GitHub

Open a terminal in your project folder and run these commands:

```bash
# Initialize git repository
git init

# Add all files to git
git add .

# Create your first commit
git commit -m "Initial commit: Personal website"

# Add GitHub as the remote origin (replace with YOUR repository URL)
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (tab at the top)
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select **GitHub Actions**
5. The workflow will run automatically on your next push

### Step 5: Verify Deployment

1. Go to the **Actions** tab in your repository
2. You should see a workflow running called "Deploy to GitHub Pages"
3. Once it completes (green checkmark), your site is live!
4. Your site URL: `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/`

## Making Updates

After making changes to your site:

```bash
# Stage your changes
git add .

# Commit with a message
git commit -m "Update research page"

# Push to GitHub
git push
```

The GitHub Action will automatically rebuild and deploy your site.

## Customization

### Colors

Edit `src/styles/global.css` and modify the CSS variables at the top:

```css
:root {
  --color-text: #2c3e50;
  --color-accent: #2a7a9b;
  /* ... */
}
```

### Fonts

The site uses [Lato](https://fonts.google.com/specimen/Lato) from Google Fonts. To change it:

1. Edit `src/layouts/BaseLayout.astro` - update the Google Fonts link
2. Edit `src/styles/global.css` - update `--font-sans`

### Layout Width

Adjust `--max-width` in `src/styles/global.css` (default: 800px).

## Troubleshooting

### Build fails on GitHub Actions

- Check the Actions tab for error messages
- Ensure your `package.json` is valid
- Verify all image paths are correct

### Images not showing

- Ensure images are in `public/images/`
- Check that filenames match exactly (case-sensitive)
- Use the correct path format: `{base}images/filename.jpg`

### 404 on deployed site

- Verify `base` in `astro.config.mjs` matches your repo name
- Make sure GitHub Pages source is set to "GitHub Actions"
- Wait a few minutes after deployment for changes to propagate

## Technology

- [Astro](https://astro.build) v5.16 - Static site generator
- [GitHub Pages](https://pages.github.com/) - Free hosting
- [GitHub Actions](https://github.com/features/actions) - Automated deployment

## License

This project is open source. Feel free to use it as a template for your own website.
