# Vyro Gear Storefront

Recovered static storefront source for `https://vyrogearstore.netlify.app/`.

## Structure

- `index.html` contains the static storefront UI.
- `admin.html` contains the Vyro 3OS-style back office for catalog edits, row ordering, campaign media slots, visitor feed display, and future Printify matching.
- `data/catalog.json` contains collections, products, draft Printify mapping fields, and variant link placeholders.
- `data/analytics.example.json` and `data/printify-catalog.example.json` document the visitor and Printify feed shapes.
- `images/` contains the recovered product and campaign images served by the existing Netlify deployment.

## Admin

Open `/admin.html` after deployment. This first version is static: it can edit/import/export catalog JSON in the browser, but it cannot securely save changes back to GitHub or Netlify by itself. To make edits save automatically and to protect the page, connect a real backend such as Netlify Identity + Functions, Supabase, or another admin service.

## Printify Wiring

Each product has legacy fields (`printify_product_id`, `printify_url`, `printify_url_verified`) plus a new structured `printify` object:

```json
{
  "product_id": null,
  "product_url": null,
  "variants": [
    {
      "size": "S",
      "color": "Cream",
      "variant_id": null,
      "url": null
    }
  ]
}
```

Set `printify.product_id`, `printify.product_url`, variant IDs/URLs where available, then set `printify_url_verified` to `true` when the product should show a live Buy on Printify button.
