# Sejong Consortium Limited — Website

Static corporate site for **[sejongconsortium.com](https://sejongconsortium.com)**. Plain HTML/CSS/JS at the repository root, ready for GitHub Pages.

## Stack

- Static pages: `index.html`, `services.html`, `about.html`, `contact.html`
- Styles: `css/styles.css`
- Light JS (mobile nav / header): `js/main.js`
- Custom domain file: `CNAME` → `sejongconsortium.com`
- `.nojekyll` so GitHub Pages serves files as-is (no Jekyll processing)

No build step and no framework.

## Local preview

From the repo root:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`.

## Enable GitHub Pages

Prefer **root of `main`** (simplest durable option for this repo).

1. Merge this site to `main` (or push directly if you prefer).
2. In the GitHub repo: **Settings → Pages**.
3. Under **Build and deployment**:
   - **Source**: Deploy from a branch
   - **Branch**: `main`
   - **Folder**: `/ (root)`
4. Save. GitHub will publish at:
   - `https://sejongconsortium.github.io/website/` (default project URL), and
   - `https://sejongconsortium.com` once DNS + custom domain are configured (see below).

The `CNAME` file in this repo tells Pages that the custom domain is `sejongconsortium.com`. After you set the same domain under **Settings → Pages → Custom domain**, GitHub will keep that file in sync.

Optional: turn on **Enforce HTTPS** after the custom domain certificate is issued (usually within minutes of correct DNS).

### Why root on `main` (not `/docs` or a PR-only deploy)

Root on `main` is the least fragile Pages setup: no docs-folder mismatch, no Actions workflow tax, and the live site always matches the default branch. Work still lands via PR so copy and design can be reviewed before go-live.

## DNS for sejongconsortium.com

Point the domain at GitHub Pages. Use either apex (`A`/`AAAA`) plus `www` (`CNAME`), or apex `ALIAS`/`ANAME` if your DNS host supports it.

### Apex (sejongconsortium.com)

Create **A** records for `@` / apex:

| Type | Name | Value |
|------|------|--------|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

Optional IPv6 **AAAA** records:

| Type | Name | Value |
|------|------|--------|
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

GitHub documents these addresses under [Configuring an apex domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain). If GitHub updates the IPs, follow their current docs.

### www (recommended redirect target)

| Type | Name | Value |
|------|------|--------|
| CNAME | `www` | `sejongconsortium.github.io` |

In **Settings → Pages → Custom domain**, enter `sejongconsortium.com` and enable **Enforce HTTPS** when available. You can set GitHub to redirect `www` ↔ apex from the Pages custom-domain UI.

### Checklist

1. DNS `A`/`AAAA` (and optional `www` `CNAME`) propagated.
2. Repo Pages source = `main` / root.
3. Custom domain = `sejongconsortium.com` (matches `CNAME` file).
4. HTTPS enforced.
5. Visit `https://sejongconsortium.com` and confirm Home / Services / About / Contact.

## Edit copy

| Page | File |
|------|------|
| Home | `index.html` |
| Services | `services.html` |
| About (corp facts) | `about.html` |
| Contact | `contact.html` |
| Shared look | `css/styles.css` |
| Nav behaviour | `js/main.js` |

Keep claims factual. Do not invent clients, testimonials, logos, team bios, or phone numbers. Contact remains `mailto:info@sejongconsortium.com` only.

## Corporate facts (source of truth)

- **Legal name:** Sejong Consortium Limited  
- **Domain:** sejongconsortium.com  
- **Federal Canadian corporation:** #8916721  
- **Registered office:** 2583 Carling Avenue, Suite 37, Ottawa ON K2B 7H7  
- **Email:** info@sejongconsortium.com  
- **Services:** Software Engineering; IT consulting  

## Image credit

Hero photograph (`assets/hero.jpg`): Unsplash — modern commercial architecture (used as atmospheric visual for a professional practice site).
