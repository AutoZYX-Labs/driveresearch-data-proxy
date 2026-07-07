# driveresearch-data-proxy

Thin GitHub Pages site bound to `data.driveresearch.tech`. It embeds the live Hugging Face Space at `https://autozyx-nds-statistics-platform.hf.space/` in a full-viewport iframe, so users land on a branded DRIVEResearch URL while still viewing the live platform.

## Why this exists

The live dashboard is hosted on Hugging Face Spaces. This repo is the smallest possible GitHub Pages site that:

1. Owns `data.driveresearch.tech` (via `CNAME` + Let's Encrypt on GH Pages).
2. Embeds the actual dashboard via iframe.
3. Falls back to a direct redirect if the iframe fails to load within 15 s.

## DNS setup (Cloudflare)

In the Cloudflare DNS console for `driveresearch.tech`, keep:

```
Type     Host    Value                      TTL
CNAME    data    autozyx.github.io.         10 min
```

Keep the record DNS-only. GitHub Pages handles HTTPS for `data.driveresearch.tech`.

Then in this repo's GitHub Settings -> Pages:
- Source: `main` branch, `/` folder
- Custom domain: `data.driveresearch.tech`
- Enforce HTTPS: enabled after the certificate is provisioned

## When the upstream Space URL changes

Edit the `src=` in `index.html` and commit. Everything else stays the same.

## Canonical links

- Main site: <https://driveresearch.tech/>
- Upstream dashboard: <https://autozyx-nds-statistics-platform.hf.space/>
- HF Space admin/viewer: <https://huggingface.co/spaces/AutoZYX/nds-statistics-platform>
- Dashboard source: <https://github.com/AutoZYX-Labs/NDS-Statistics-Platform>
