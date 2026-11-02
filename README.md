# presentingwithimpact.com

The book site for **Presenting with Impact: A Practical Guide to Effective Communication** by
Pendleton B. Wickersham, MD, FACP, FACR, published by
[Brewster Wickersham Publications](https://brewsterwickershampublications.com/).
Plain static HTML and CSS for GitHub Pages. No build step — edit and push.

| File | What it is |
| --- | --- |
| `index.html` | The whole site: hero, the ten chapters, who it's for, the author, order, publisher network |
| `site.css` | Shared styles. Palette sampled from the printed cover: navy `#1C2C4D`, amber `#DC9B37`, white |
| `404.html` | Not-found page (`noindex`, root-relative links) |
| `images/cover.jpg` | Front cover, 800×1200, from the published KDP cover |
| `images/og-image.jpg` | 1200×630 social share card |
| `images/icon.png`, `apple-touch-icon.png`, `favicon.png` | Waveform mark on navy, drawn from the cover motif |
| `images/author-wickersham.jpg` | Author photo (same one used on theresilientpathbook.com) |
| `CNAME` | Custom domain for GitHub Pages. **Do not delete.** |
| `.nojekyll` | Stops GitHub running Jekyll over the files |
| `robots.txt`, `sitemap.xml` | Crawl rules and sitemap; bump `<lastmod>` when the page changes |

Preview locally with `python -m http.server` in this folder, then open http://localhost:8000.

## The book

| | |
| --- | --- |
| Paperback | [B0HQ2JQ6SQ](https://www.amazon.com/dp/B0HQ2JQ6SQ) · ISBN 979-8167073890 · 99 pages · 6×9 |
| Kindle | [B0HQ1P6CZH](https://www.amazon.com/dp/B0HQ1P6CZH) · 107 pages |
| Published | November 1, 2026 |

Both Amazon links appear in three places per page: the hero buttons, the order section, and the
footer network block — plus the JSON-LD `workExample` entries. Keep them in step.

## Status

Live at https://presentingwithimpact.com/ (GitHub Pages, custom domain, DNS at GoDaddy).
The page carries canonical, Open Graph and Twitter tags, and WebSite + Organization + Person + Book
JSON-LD. The author's `@id` is shared with theresilientpathbook.com so search engines treat it as
one person across both sites.

## DNS (GoDaddy)

This domain's nameservers are GoDaddy's (`ns31/ns32.domaincontrol.com`), unlike the other
Brewster Wickersham domains, which are at Porkbun. Manage it in GoDaddy → My Products →
presentingwithimpact.com → **DNS**.

The apex is canonical, matching theresilientpathbook.com.

1. **Turn off domain forwarding / parking first.** GoDaddy re-adds its own A records while
   forwarding is on, which will fight the records below.
2. **Delete** the parked apex `A` records (they pointed at `3.33.130.190` and `15.197.148.33`).
3. **Add four `A` records**, Name `@`:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

4. **Add four `AAAA` records**, Name `@` (optional but recommended):

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

5. **Replace the `www` CNAME.** It currently points at the apex; it should point at:

```
pennwickersham.github.io
```

Leave any MX or TXT records alone if email is ever added to this domain.

Then in Settings → Pages, wait for the certificate to issue and tick **Enforce HTTPS**. If the
cert sticks on "DNS check" for more than about half an hour, remove and re-add the custom domain
via the Pages API — that is what unstuck arcaneestategame.com.

Check with:

```bash
nslookup presentingwithimpact.com 8.8.8.8
```

## Still to do

1. **Search Console / Bing Webmaster Tools** — verify by DNS TXT and submit
   `https://presentingwithimpact.com/sitemap.xml`.
2. **Reviews** — once the book has a few, consider a short quotes section above the order block.
